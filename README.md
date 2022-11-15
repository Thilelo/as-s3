# Como instalar e configurar o DHCP no Ubuntu 20.04
## - Passo 1
Verificar a versão do Ubuntu utilizada, no terminal execute:
`lsb_release -a`
## - Passo 2
Instalar o servidor DHCP com o seguinte comando:
`sudo apt install isc-dhcp-server`
## - Passo 3
Insira a letra "S" para confirmar o download e a instalação do serviço:
`S`
## - Passo 4
Configurar a placa de rede, deve-se editar o arquivo "isc-dhcp-server" para definir os valores associados à placa de rede e assim oferecer de forma abrangente o que o DHCP oferece:
`sudo nano / etc / default / isc-dhcp-server`
