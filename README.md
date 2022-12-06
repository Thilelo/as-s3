# Como instalar e configurar o DHCP no Ubuntu 20.04
## - Passo 1
Verificar a versão do Ubuntu utilizada, execute no terminal:

`lsb_release -a`
## - Passo 2
Instalar o servidor DHCP com o seguinte comando:

`sudo apt install isc-dhcp-server`
## - Passo 3
Insira a letra "S" para confirmar o download e a instalação do serviço:

`S`
## - Passo 4
Configurar a placa de rede, deve-se editar o arquivo "isc-dhcp-server" para definir os valores associados à placa de rede e assim oferecer de forma abrangente o que o DHCP oferece:

`sudo nano /etc/default/isc-dhcp-server`

![This is an image](https://cdn.smartworldclub.net/4685118/_instalar_y_configurar_servidor_dhcp_en_ubuntu_2104_y_2004_5.png.webp)

## - Passo 5
Essas linhas que vemos são:
- INTERFACESv4: configurar o endereçamento IPv4 
- INTERFACESv6: configurar o endereçamento IPv6

Lá é necessário saber o ID da placa de rede, por isso devemos fazer o seguinte:

`adicionar ip`

![This is an image](https://cdn.smartworldclub.net/4685118/_instalar_y_configurar_servidor_dhcp_en_ubuntu_2104_y_2004_6.png.webp)

## - Passo 6
Neste caso é "ens33", na seção INTERFACESv4 adicionamos este ID:

![This is an image](https://cdn.smartworldclub.net/4685118/_instalar_y_configurar_servidor_dhcp_en_ubuntu_2104_y_2004_6.png.webp)

Salvamos as alterações com as teclas Ctrl + O e saímos do editor com as teclas Ctrl + X.

## - Passo 7
Depois disso, vamos configurar a função DHCP no Ubuntu 20.04 ou 21.04, é possível configurar:
 - Endereços de servidor DNS
 - Intervalo de endereços a ser usado
 - Máscara de sub-rede
 - Tempo de atividade do endereço
 - Porta de entrada
 
Acessamos o arquivo de configuração:

 `sudo nano /etc/dhcp/dhcpd.conf`
 ## - Passo 8
Lá vamos adicionar as seguintes linhas com os valores necessários:

`sub-rede 192.168.xxx.xxx máscara de rede 255.255.255.0 intervalo 192.168.xxx.xxx; opção de servidores de nomes de domínio 8.8.8.8, 4.4.4.4; opção nome de domínio "nome"; roteadores de opção 192.168.xxx.xxx; opção de endereço de transmissão 192.168.xxx.255; default-lease-time 600; tempo máximo de locação 7200;`

Salvamos as alterações com Ctrl + O e saímos com Ctrl + X.
## - Passo 9
Neste arquivo, adicionamos o endereço IP e a máscara de rede do servidor DHCP. 

Estabelecemos o intervalo de endereços a serem entregues, o DNS público foi configurado, inserimos o nome de domínio e o endereço de transmissão foi estabelecido.

Agora executamos o seguinte:

`sudo systemctl start isc-dhcp-server` (inicia serviço DHCP)

`sudo systemctl stop isc-dhcp-server` (para serviço DHCP)

![This is an image](https://cdn.smartworldclub.net/4685118/_instalar_y_configurar_servidor_dhcp_en_ubuntu_2104_y_2004_10.png.webp)
## - Passo 10
Para verificar se tudo funciona corretamente, em um computador cliente validamos os dados da placa de rede com o seguinte comando:
`adicionar ip`
## - Passo 11
Acessamos o arquivo de configuração DHCP:
`sudo nano /etc/dhcp/dhcpd.conf`

Neste arquivo, inserimos o seguinte:

`Ubuntu host localhost`
`hardware ethernet "endereço MAC"`
`endereço fixo 192.168.xxx.xxx;`

Observação: Este é um IP reservado para este computador.
## - Etapa 12
Salvamos as alterações no arquivo, vamos para a área de trabalho do Ubuntu e clicamos no ícone Network, lá clicamos em "Wired conectado - Wired network configuration":

![This is an image](https://cdn.smartworldclub.net/4685118/_instalar_y_configurar_servidor_dhcp_en_ubuntu_2104_y_2004_13.png.webp)
 ## - Etapa 13
O seguinte será exibido:

![This is an image](https://cdn.smartworldclub.net/4685118/_instalar_y_configurar_servidor_dhcp_en_ubuntu_2104_y_2004_14.png.webp)

- Fonte: [Smartworldclub.net](https://smartworldclub.net/11703951-install-and-configure-dhcp-server-in-ubuntu-21-04-and-20-04)
