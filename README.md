*A entrega de conteúdo de forma customizada requer habilidades de desenvolvimento.

Esse tipo de integração é utilizada quando a entrega de conteúdo requer operações avançadas e especificas ou a entrega seja através de plataforma própria.

Para isso é necessário seguir os seguintes passos:

1- É necessário configurar uma URL que receberá o post no cadastro de conteúdo na Eduzz.
Dentro do cadastro do seu conteúdo existe uma sessão chamada 'Entrega/Ativação', selecione a opção 'Customizada' no campo 'Integração para Entrega de Conteúdo' e configure o campo 'URL' com a url que receberá o POST na entrega desse conteúdo, após ser vendido.

2- Quando houver uma entrega a URL configurada no cadastro do conteúdo receberá um POST com os seguintes campos.

* **edz_fat_cod:** Código da Fatura que originou a entrega
* **edz_cnt_cod:** Código do conteúdo que o cliente final comprou na Eduzz
* **edz_cli_cod:** Código do Cliente que efetuou o pagamento da fatura na Eduzz
* **edz_cli_rsocial:** Nome do Cliente que efetuou o pagamento da fatura na Eduzz
* **edz_cli_email:** E-mail do Cliente que efetuou o pagamento da fatura na Eduzz
* **edz_cli_cel:** Celular do Cliente que efetuou o pagamento da fatura na Eduzz
* **edz_fat_dtcadastro:** Data de geração da fatura na Eduzz
* **edz_gtr_dist:** Código do Afiliado que realizou a venda do conteúdo na Eduzz
* **edz_gtr_param1:** Parâmetros opcionais enviados via GET (p1) no redirecionamento para o checkout
* **edz_gtr_param2:** Parâmetros opcionais enviados via GET (p2) no redirecionamento para o checkout
* **edz_gtr_param3:** Parâmetros opcionais enviados via GET (p3) no redirecionamento para o checkout
* **edz_gtr_param4:** Parâmetros opcionais enviados via GET (p4) no redirecionamento para o checkout
* **edz_gtr_param5:** Parâmetros opcionais enviados via GET (p5) no redirecionamento para o checkout
* **edz_valorpago:** Valor pago pelo cliente

3- Fora os campos citados na tabela é enviado um campo chamado sid que é a chave de autenticação do envio. É através dela que seu sistema poderá reconhecer essa requisição como uma requisição válida.

A lógica para geração do sid é a seguinte:
- Ordene todos os campos recebidos por nome e colocar os valores em uma string.
-  No final dessa string adicione sua API KEY (também mostrada no cadastro de conteúdo) e adicione no final da string
- Por último criptografe essa string com a criptografia MD5 e pronto, você tem a sid para comparar com a sid enviada por nós e autenticar essa requisição como válida.


Outra opção de validacão é através do campo 'nsid':
Verificar se o campo nsid é igual a SHA1(edz_fat_cod + edz_cnt_cod + edz_cli_cod)
