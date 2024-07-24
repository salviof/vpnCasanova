# Vpn Casanova

Projeto Open-VPN Casanova

## Estrutura de diretórios

Arquivos ambiente de servidor:

./dockerFileServer/Dockerfile  -> Arquivo imagem docker 
./dockerFileServer/arquivos -> Scripts de instalação


Arquivos ambiente cliente

./dockerFileClient/Dockerfile -> Arquivo imagem docker 
./dockerFileClient/arquivos -> Scripts de instalação


## Variaveis de ambiente

Servidor:

VPN_SRV_CHAVE_DE_ACESSO
VPN_SRV_DOMINIO_ENDPOINT
VPN_SRV_IPS_AUTORIZADOS (Lista deve ser configurada no OpenVpn)
VPN_SRV_PORTA_CONEXÃO (Havendo diversas portas para o funcionamento do VPN, nomear especificando a funação exemplo PORTA_CONEXAO, PORTA_FUNÇÃO... )
VPN_SRV_IP_PUBLICO

CLIENTE:

VPN_CHAVE_DE_ACESSO
VPN_HOST_SERVIDOR
VPN_ID_CLIENTE
VPN_REDE_VPN



## Comportamento entrypoint do cliente:

1-> O cliente acessa um serviço web informando: CHAVE_DE_ACESSO,  ID_CLIENTE, e REDE_VPN 
2-> O servidor retorna 200 com o conteúdo do arquivo de configuração do vpn ou retorna 401, com acesso negado.
3-> No Entrypoint do docker client o cliente salva o o conteúdo recebido e para se conectar com o cliente.
4-> O cliente testa a conexão do vpn e caso não esteja conectado gera um erro que impede a execução da imagem.

## Referência:

https://dockovpn.io/docs/quickstart/ (Projeto simlar)
https://openvpn.net/as-docs/docker.html (Documentação Openvepn Server)

## License

[MIT](https://choosealicense.com/licenses/mit/)
