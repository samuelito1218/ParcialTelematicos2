# Segundo Parcial - Servicios Telemáticos
Universidad Autónoma de Occidente - 2026

## Integrantes
- Samuel Arredondo Delgado - Código 2226528
- Angélica María Marcillo Alba - Código 2225347

## Topología
- **server1** (192.168.50.3) - Firewall UFW + reenvío de puertos
- **server2** (192.168.50.2) - vsftpd FTPS + OpenSSH SFTP
- **client** (192.168.50.4) - DNS over TLS + cliente SFTP

## Servicios implementados
1. FTPS protegido por Firewall UFW
2. DNS sobre TLS (DoT)
3. SFTP protegido por Firewall UFW

## Contenido del repositorio
- `Vagrantfile` - Configuración de las 3 VMs
- `ftps/vsftpd.conf` - Configuración vsftpd con TLS explícito
- `ufw/before.rules` - Reglas NAT para reenvío de puertos
- `dot/resolved.conf` - Configuración DNS over TLS
- `ftps.pcap` - Captura Wireshark FTPS
- `sftp.pcap` - Captura Wireshark SFTP

## Tabla comparativa FTPS vs SFTP

| Criterio | FTPS | SFTP |
|---|---|---|
| Protocolo base | FTP + TLS/SSL | SSH (OpenSSH) |
| Nro. de puertos | 2+ (21 + 50000-50010) | 1 solo (puerto 22) |
| Certificado | SSL/TLS X.509 (OpenSSL) | Claves SSH o contraseña |
| Cifrado | TLS explícito: inicia texto claro, luego AUTH TLS | Todo cifrado desde el primer paquete |
| Wireshark muestra | AUTH TLS → Client Hello → Application Data | Solo SSHv2 Encrypted packet |
| Firewall | Difícil: rango pasivos 50000-50010 | Fácil: solo puerto 22 |
| Configuración | Media: vsftpd + certs + NAT | Alta: OpenSSH preinstalado |