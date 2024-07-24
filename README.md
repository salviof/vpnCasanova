# Vpn Casanova

Projeto Open-VPN Casanova

## Estrutura de diretórios

### Arquivos ambiente de servidor:

./dockerFileServer/Dockerfile  -> Arquivo imagem docker <br>
./dockerFileServer/arquivos -> Scripts de instalação <br>


### Arquivos ambiente cliente

./dockerFileClient/Dockerfile -> Arquivo imagem docker <br>
./dockerFileClient/arquivos -> Scripts de instalação <br>


## Variaveis de ambiente

### Servidor:

VPN_SRV_CHAVE_DE_ACESSO <br>
VPN_SRV_DOMINIO_ENDPOINT <br>
VPN_SRV_IPS_AUTORIZADOS (Lista deve ser configurada no OpenVpn) <br>
VPN_SRV_PORTA_CONEXÃO (Havendo diversas portas para o funcionamento do VPN, nomear especificando a funação exemplo PORTA_CONEXAO, PORTA_FUNÇÃO... ) <br>
VPN_SRV_IP_PUBLICO<br>

### CLIENTE:

VPN_CHAVE_DE_ACESSO (É a chave para obter o arquivo de configuração do openvpn, <br>
VPN_HOST_SERVIDOR<br>
VPN_ID_CLIENTE<br>
VPN_REDE_VPN<br>



## Comportamento entrypoint do cliente:

1-> O cliente verifica se existe um arquivo de configuração com as variaveis de ambiente enviadas, se existir não faz nada,
se existir uma configuração com outra configuração, apaga a configuração antiga.
uma vez que esteja sem o arquivo de configuração, O cliente acessa um serviço web informando: CHAVE_DE_ACESSO,  ID_CLIENTE, e REDE_VPN <br>
2-> O servidor retorna 200 com o conteúdo do arquivo de configuração do vpn ou retorna 401, com acesso negado.<br>
3-> No Entrypoint do docker client o cliente salva o o conteúdo recebido e para se conectar com o cliente.<br>
4-> O cliente testa a conexão do vpn e caso não esteja conectado gera um erro que impede a execução da imagem.<br>

## Referência:

https://dockovpn.io/docs/quickstart/ (Projeto simlar)<br>
https://openvpn.net/as-docs/docker.html (Documentação Openvepn Server)<br>

## License

[MIT](https://choosealicense.com/licenses/mit/)
