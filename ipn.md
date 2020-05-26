# Mensagem enviada no IPN da Quivra

Essa é o Body do Post que enviarmos no nosso PostBack (IPN)

A notificação de pagamento instantâneo (IPN) é um método para os varejistas on-line rastrearem automaticamente compras e outras comunicações entre servidores em tempo real.
Isso permite que os sistemas de comércio eletrônico tenham a oportunidade de armazenar transações de pagamento, informações sobre pedidos e outras vendas internamente.
As mensagens IPN podem representar êxito ou falhas no pagamento, alterações no status da transação do pedido, informações do razão contábil e muitas outras.

A Url pode ser configurada no seu painel de controle em Ferramentas / Post Back (IPN), você pode enviar o IPN para qualquer status de transaação e forma de pagamento


```json
{
	"checkoutUuid":"IDENTIFICADOR UNICO DA QUIVRA",
	"totalCheckout": "1.00",
	"totalProducts" : "1.00",
	"totalFrete": "0.00",
	"statusCheckout": "1",
	"statusName": "Iniciado",
	"paymentType" : "1",
	"paymentTypeName": "Cartao de Credito",
	"customer": {
		"customerName": "NOME DO CONSUMIDOR",
		"customerDocument": "NUMERO DO CPF",
		"customerEmail": "EMAIL DO CONSUMIDOR",
		"customerMobile": "NUMERO DO CELULAR",
		"customerOtherPhone": "OUTRO TELEFONE", // QUANDO INFORMADO PELO CONSUMIDOR
		"address" : {
			"street": "ENDERECO",
			"number": "NUMERO DA RESIDENCIA",
			"complement": "COMPLEMENTO",
			"neighborhood": "BAIRRO",
			"city": "CIDADE",
			"county": "ESTADO",
			"zipCode": "CEP",
			"deliveryTo": "NOME DO RECEBEDOR ", // QUANDO DIFRERENTE DO COMPRADOR
		}
	},
	"products": [
		{
			"productUuid": "CODIGO INTERNO DO PRODUTO",
			"planUuid": "CODIGO INTERNO DO PLANO",
			"productName": "NOME DO PRODUTO",
			"planName": "NOME DO PLANO",
			"productQty": "QUANTIDADE COMPRA",
			"valueProduct": "VALOR UNITARIO",
			"totalProduct": "TOTAL DESTE PRODUTO",
		}
	],
	"payment": {
		"creditCard": [
			{	
				"cardBin": "5555 **** **** 5555",
				"cardType": "Master",
				"cardName": "NOME NO CARTAO",
				"cardDocument": "CPF DO TITULAR",
				"cardExpiry": "DATA DE EXPIRAÇÃO DO CARTAO MM/AAAA",
				"installments": "QUANTIDADE DE PARCELAS",
				"authorizationCode": "CODIGO DE AUTORIZACAO DO CARTAO"
			}
		],
		"boleto": {
			"barCode": "CODIGO DE BARRAS FEBRABAM",
			"digitableLine": "LINHA DIGITAVEL DO BOLETO",
			"urlBoleto": "URL DE IMPRESSAO DO BOLETO",
			"dueData": "DATA DE VENCIMENTO (AAAA-MM-DD)"

		},
		"debitCard": {  
			"cardBin": "5555 **** **** 5555",
			"cardType": "Master",
			"cardName": "NOME NO CARTAO",
			"cardDocument": "CPF DO TITULAR",
			"cardExpiry": "DATA DE EXPIRAÇÃO DO CARTAO MM/AAAA",
			"authorizationCode": "CODIGO DE AUTORIZACAO DO CARTAO"
		},
		"wireTransfer": {
			"paymentProof": "URL DO COMPROVANTE DO PAGAMENTO",
			"paymentStatus": "0", //(0 - AGUARDANDO, 1 - CONFIRMADA)
		},
		"bitcoins": {
			"walletAddress": "ENDERECO DA CARTEIRA BTC",
			"valueBTC": "VALOR CONVERTIDO EM BITCOINS",
			"receivedValue": "VALOR RECEBIDO PELA CARTEIRA ATE O MOMENTO",
			"btcStatus": "0", //(0 - AGUARDANDO, 1 - CONFIRMADA)
		},
		"paypal": {
			"statusPayment":  "0", //(0 - AGUARDANDO, 1 - CONFIRMADA)
			"authorizationCode": "CÓDIGO DE AUTORIZAÇÃO DO PAYPAL"

		},
		"quivra": {
			"statusPayment": "0", //(0 - AGUARDANDO, 1 - CONFIRMADA)
			"transactionUuid": "IDENTIFICADOR UNICO NA QUIVRA"
		},
		"googleWalelt": {
			"statusPayment":  "0", //(0 - AGUARDANDO, 1 - CONFIRMADA)
			"authorizationCode": "CÓDIGO DE AUTORIZAÇÃO DO GOOGLE PAY"
		},
		"applePay": {
			"statusPayment":  "0", // (0 - AGUARDANDO, 1 - CONFIRMADA)
			"authorizationCode": "CÓDIGO DE AUTORIZAÇÃO DO APPLE PAY" 
		}
	},
	"fraudAnalytcs": {
		"score" : "0", //Pontos no Score
		"fraudStatus": "STATUS DA ANALISE DE FRAUDE"
	},
	"blockchain": {
		"sessionId": "IDENTIFICADOR UNICO DA SESSAO DO CONSUMIDOR",
		"node": "IDENTIFICADOR DO NÓ QUE RECEBEU A TRANSACAO",
		"confirmations": "CONFIRMACOES DA REDE INTERNA",
		"transactionHash": "IDENTIFICADOR DA TRANSACAO",
		"fraudAnalytcsHash": "IDENTIFICADOR DO ANTI-FRAUDE",
		"customerHash": "IDENTIFICADOR UNICO DO CONSUMIDOT"
	},
	"saleInformation": {
		"affiliates": [
			{
				"affiliateUuid": "IDENTIFICADOR DO AFILIADO",
				"affiliateName": "NOME DO AFILIADO",
				"afiiliateEmail": "EMAIL DO AFILIADO",
				"clickNumer": "FIRST, LAST, INTERMEDIATE", // primeiro click, ultimo ou intermediário
				"comissionValue": "0.00"
			}
		],
		"coProducer": [
			{
				"coProducerUuid": "IDENTIFICADOR DO CO-PRODUTOR",
				"coProducerName": "NOME DO CO-PRODUTOR",
				"coProducerEmail": "EMAIL DO CO-PRODUTOR",
				"comissionValue": "0.00"
			}
		],
		"manager": [
			{
				"managerUuid": "IDENTIFICADOR DO GERENTE",
				"managerName": "NOME DO GERENTE",
				"managerEmail": "EMAIL DO GERENTE",
				"comissionValue": "0.00"
			}
		],
		"quivra": {
			"comission": "0.00",
			"transactionFee": "0.00",
			"estimatedCreditDate": "AAAA-MM-DD"
		}

	}		
}
```
# Status dos Pagamentos:
1  - INICIADO<br />
2  - AGUARDANDO ANALISE<br />
3  - APROVADO<br />
4  - FINALIZADO<br />
5  - REPROVADO<br />
6  - CHARGEBACK<br />
7  - EM DISPUTA<br />
8  - AGUARDANDO PAGAMENTO<br />
9  - CANCELADO<br />
10 - ABANDONADO<br />
11 - EXPIRADO<br />
12 - REEMBOLSADO<br />
13 - ENTREGA INFORMADA<br />

# Tipos de Pagamentos:
1  - CARTÃO DE CRÉDITO<br />
2  - DOIS CARTOES DE CREDITO<br />
3  - CARTAO DE CREDITO E BOLETO<br />
4  - CARTAO DE DÉBITO<br />
5  - BOLETO BANCARIO<br />
6  - TRANSFERENCIA<br />
7  - BITCOINS<br />
8  - PAYPAL<br />
9  - GOOGLE WALLET<br />
10 - APPLE PAY<br />
11 - QUIVRA (SALDO NA PLATAFORMA)<br />
