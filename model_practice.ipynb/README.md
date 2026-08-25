{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyOp5EQJb49LBPuxa4LKBVWE",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/192511202simats-ctrl/CSA63-THREAT-INTELLIGENCE-AND-NETWORK-SEC/blob/main/model_practice\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "code",
      "execution_count": 1,
      "metadata": {
        "colab": {
          "base_uri": "https://localhost:8080/"
        },
        "id": "SGy7CBCkDKBB",
        "outputId": "7819dbb4-76a2-44cf-c0da-6216ce2e2b44"
      },
      "outputs": [
        {
          "output_type": "stream",
          "name": "stdout",
          "text": [
            "Describe the business scenario: A bank wants to detect suspicious credit card transactions and prevent online fraud.\n",
            "Application area: Banking fraud prevention\n"
          ]
        }
      ],
      "source": [
        "# CSA63 Practical Questions - Python Programs 1-40\n",
        "# Based on the uploaded practical-question sheet.\n",
        "\n",
        "# 1. Threat-intelligence application area\n",
        "def q1():\n",
        "    s = input(\"Describe the business scenario: \").lower()\n",
        "    if any(x in s for x in [\"bank\", \"payment\", \"credit\", \"transaction\"]):\n",
        "        print(\"Application area: Banking fraud prevention\")\n",
        "    elif any(x in s for x in [\"hospital\", \"healthcare\", \"patient\", \"medical\"]):\n",
        "        print(\"Application area: Healthcare data protection\")\n",
        "    elif any(x in s for x in [\"shop\", \"ecommerce\", \"online store\", \"cart\"]):\n",
        "        print(\"Application area: E-commerce fraud prevention\")\n",
        "    else:\n",
        "        print(\"Application area: General enterprise threat intelligence\")\n",
        "q1()"
      ]
    },
    {
      "cell_type": "code",
      "source": [
        "# 2. Simple vulnerability assessment - port scanner\n",
        "import socket\n",
        "def q2():\n",
        "    host = input(\"Enter target host: \")\n",
        "    ports = [21, 22, 23, 25, 53, 80, 110, 135, 139, 143, 443, 445, 3389]\n",
        "    for port in ports:\n",
        "        s = socket.socket()\n",
        "        s.settimeout(0.3)\n",
        "        if s.connect_ex((host, port)) == 0:\n",
        "            print(\"Open:\", port)\n",
        "        s.close()\n",
        "# q2()\n"
      ],
      "metadata": {
        "id": "dNkE0MvjD3mB"
      },
      "execution_count": 3,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# 3. Security policy governance checker\n",
        "def q3():\n",
        "    text = input(\"Paste policy text: \").lower()\n",
        "    required = [\"scope\", \"roles and responsibilities\", \"enforcement\",\n",
        "                \"review cycle\", \"approval authority\"]\n",
        "    for item in required:\n",
        "        print((\"FOUND: \" if item in text else \"MISSING: \") + item)\n",
        "# q3()"
      ],
      "metadata": {
        "id": "rBXZu7Q5E5dh"
      },
      "execution_count": 4,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# 4. VPN confidentiality demonstration using XOR stream cipher\n",
        "import secrets\n",
        "def q4():\n",
        "    data = input(\"Enter message: \").encode()\n",
        "    key = secrets.token_bytes(len(data))\n",
        "    encrypted = bytes(a ^ b for a, b in zip(data, key))\n",
        "    decrypted = bytes(a ^ b for a, b in zip(encrypted, key))\n",
        "    print(\"Captured ciphertext:\", encrypted.hex())\n",
        "    print(\"Without key: unreadable ciphertext\")\n",
        "    print(\"With shared key:\", decrypted.decode())\n",
        "# q4()"
      ],
      "metadata": {
        "id": "S-zYGpVbFA0M"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# 5. Threat-intelligence report classifier\n",
        "def q5():\n",
        "    text = input(\"Report description/audience: \").lower()\n",
        "    if any(x in text for x in [\"executive\", \"board\", \"business risk\", \"strategy\"]):\n",
        "        print(\"Strategic\")\n",
        "    elif any(x in text for x in [\"tactic\", \"technique\", \"ttp\", \"campaign\"]):\n",
        "        print(\"Tactical\")\n",
        "    else:\n",
        "        print(\"Operational\")\n",
        "# q5()"
      ],
      "metadata": {
        "id": "qEzFKvImFFLL"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# 6. Phishing URL detector\n",
        "from urllib.parse import urlparse\n",
        "def q6():\n",
        "    url = input(\"Enter URL: \")\n",
        "    p = urlparse(url)\n",
        "    host = p.netloc.lower()\n",
        "    score = 0\n",
        "    reasons = []\n",
        "    if any(k in url.lower() for k in [\"login\", \"verify\", \"update\", \"secure\", \"account\"]):\n",
        "        score += 1; reasons.append(\"suspicious keyword\")\n",
        "    try:\n",
        "        socket.inet_aton(host.split(\":\")[0])\n",
        "        score += 2; reasons.append(\"IP-based domain\")\n",
        "    except:\n",
        "        pass\n",
        "    if host.count(\".\") >= 3:\n",
        "        score += 1; reasons.append(\"excessive subdomains\")\n",
        "    if p.scheme != \"https\":\n",
        "        score += 1; reasons.append(\"not HTTPS\")\n",
        "    print(\"PHISHING\" if score >= 2 else \"LIKELY LEGITIMATE\")\n",
        "    print(\"Reasons:\", \", \".join(reasons) if reasons else \"none\")\n",
        "# q6()\n",
        "\n"
      ],
      "metadata": {
        "id": "1RUZIlQKFJ_F"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [
        "# 7. ELK-style parsing, indexing and aggregation\n",
        "import re\n",
        "def q7():\n",
        "    logs = [\n",
        "        \"2026-08-25 09:00 INFO user=alice action=login\",\n",
        "        \"2026-08-25 09:01 ERROR user=bob action=login\",\n",
        "        \"2026-08-25 09:02 ERROR user=bob action=login\"\n",
        "    ]\n",
        "    index = []\n",
        "    for line in logs:\n",
        "        m = re.search(r\"(\\S+ \\S+) (\\w+) user=(\\w+) action=(\\w+)\", line)\n",
        "        if m:\n",
        "            index.append({\"time\":m.group(1),\"level\":m.group(2),\n",
        "                          \"user\":m.group(3),\"action\":m.group(4)})\n",
        "    counts = {}\n",
        "    for e in index:\n",
        "        counts[e[\"level\"]] = counts.get(e[\"level\"], 0) + 1\n",
        "    print(\"Indexed events:\", index)\n",
        "    print(\"Kibana-style aggregation:\", counts)\n",
        "# q7()\n"
      ],
      "metadata": {
        "id": "-GGC7QEZFLlF"
      },
      "execution_count": null,
      "outputs": []
    },
    {
      "cell_type": "code",
      "source": [],
      "metadata": {
        "id": "YlQITN9OFRwY"
      },
      "execution_count": null,
      "outputs": []
    }
  ]
}
