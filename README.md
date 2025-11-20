
BANNER = r"""
██╗     ██╗   ██╗ █████╗ ██╗        ██████╗ ███╗   ██╗███████╗
██║     ██║   ██║██╔══██╗██║        ██╔══██╗████╗  ██║██╔════╝
██║     ██║   ██║███████║██║        ██████╔╝██╔██╗ ██║█████╗  
██║     ██║   ██║██╔══██║██║        ██╔══██╗██║╚██╗██║██╔══╝  
███████╗╚██████╔╝██║  ██║███████╗   ██████╔╝██║ ╚████║███████╗
╚══════╝ ╚═════╝ ╚═╝  ╚═╝╚══════╝   ╚═════╝ ╚═╝  ╚═══╝╚══════╝
                   OSINT SCANNER v1.0
"""

print(BANNER)


def whois_lookup(domain):
    try:
        data = whois.whois(domain)
        return data
    except:
        return "Erro na consulta WHOIS."


def http_info(url):
    try:
        r = requests.get(url, timeout=5)
        return {
            "status": r.status_code,
            "headers": r.headers,
            "elapsed": r.elapsed.total_seconds()
        }
    except:
        return "Erro ao acessar o arquivo.