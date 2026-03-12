# 🚀 Generating CSV and ZIP Files from Multiple Sources
### SAP BTP Integration Suite (CPI)

Projeto de laboratório desenvolvido durante meus estudos em **SAP BTP – Integration Suite (Cloud Integration)**.

O objetivo deste projeto é demonstrar como construir um **iFlow capaz de consumir dados de múltiplas fontes, converter os dados em CSV e gerar um arquivo ZIP contendo múltiplos arquivos**.

Esse tipo de cenário é comum em **integrações empresariais**, quando precisamos consolidar dados provenientes de diferentes sistemas e gerar arquivos para parceiros externos ou sistemas legados.

![Capa](imagens/capa-linkedin.png)

---

# 🧩 Integration Scenario

A integração utiliza **duas fontes de dados diferentes**:

1️⃣ Payload enviado via **Postman (XML)**  
2️⃣ Dados consumidos de uma **API OData pública**

API utilizada:


https://services.odata.org/V4/TripPinServiceRW/Airports


Essa API retorna **informações sobre aeroportos**.

---

# 🏗 iFlow Architecture

O fluxo foi desenvolvido utilizando **SAP Integration Suite – Cloud Integration (CPI)**.

Fluxo da integração:




Esses componentes são muito utilizados em projetos reais de integração.


O arquivo **ZIP é enviado automaticamente para um servidor SFTP**.

---

# 🔧 Technologies Used

Nesse laboratório utilizei alguns componentes importantes do **SAP Integration Suite (CPI)**:

- HTTPS Sender Adapter
- Content Modifier
- Request Reply
- OData API
- Parallel Multicast
- XML to CSV Converter
- Join
- Gather (ZIP Aggregation)
- SFTP Receiver

Esses componentes são **muito utilizados em projetos reais de integração**.

---

# 📥 Example Payload (Postman)

Exemplo do payload enviado via Postman:

```xml
<Airports>
   <Airport>
      <IataCode>LHR</IataCode>
      <IcaoCode>EGLL</IcaoCode>
      <Name>London Heathrow Airport</Name>
      <City>London</City>
      <Country>United Kingdom</Country>
   </Airport>
</Airports>
```

📤 Resultado gerado pela integração

A integração gera dois arquivos CSV e os compacta automaticamente em um arquivo ZIP.
```
Airport.zip
 ├── Airport1.csv  (dados do Postman)
 └── Airport2.csv  (dados da API TripPin)
```
Esses arquivos são enviados automaticamente para um servidor SFTP.

🎯 Conceitos praticados

Durante esse laboratório foi possível praticar conceitos importantes de integração:

✔ Consumo de API OData

✔ Manipulação de payloads

✔ Uso de Exchange Properties

✔ Processamento paralelo com Multicast

✔ Conversão XML → CSV

✔ Geração de arquivos ZIP

✔ Integração com SFTP


<br><br><br>
📊 Exemplo Prático do Fluxo

### Criando nosso Iflow
![Fluxo](imagens/Screenshot_1.png)

<br><br><br>


### Criando nosso Artifacts
![Fluxo](imagens/Screenshot_2.png)
```
Generating CSV and ZIP Files from Multiple Sources
```
<br><br><br>
### Adicionando o HTTPS
![Fluxo](imagens/Screenshot_3.png)

<br><br><br>
### Criando nosso Endpoint
![Fluxo](imagens/Screenshot_4.png)
```
/generating/csv
```
<br><br><br>
### Adicionar o Content Modifier
![Fluxo](imagens/Screenshot_5.png)

<br><br><br>
### Renomeando o Content Modifier
![Fluxo](imagens/Screenshot_6.png)
```
originalPayload
```

<br><br><br>
### Capturando a mensagem no Property no Content Modifier
![Fluxo](imagens/Screenshot_7.png)
```
Content Modifier originalPayload
Exchange Property
Name: _originalPayload
Type: Expression
Value: ${body}
Data Type: java.lang.String
```

<br><br><br>
### Adicionando um novo Receiver
![Fluxo](imagens/Screenshot_8.png)

<br><br><br>
### Renomeando o Receiver
![Fluxo](imagens/Screenshot_9.png)
```
ODATAv4
```

<br><br><br>
### Adicionando o Request Replay
![Fluxo](imagens/Screenshot_10.png)

<br><br><br>
### Selecionando o oData
![Fluxo](imagens/Screenshot_11.png)

<br><br><br>
### Selecionando o oData V4
![Fluxo](imagens/Screenshot_12.png)

<br><br><br>
### Renomeando o Receiver
![Fluxo](imagens/Screenshot_13.png)
```
Address: https://services.odata.org/V4/(S(okozo2a42m22jenurt2qhucs))/TripPinServiceRW
```

<br><br><br>
### Configurando o oDATA
![Fluxo](imagens/Screenshot_14.png)

<br><br><br>
### Configurando o System e Endereço
![Fluxo](imagens/Screenshot_15.png)
```
Address: https://services.odata.org/V4/(S(okozo2a42m22jenurt2qhucs))/TripPinServiceRW
```

<br><br><br>
### Selecionando a Entidade do Airports
![Fluxo](imagens/Screenshot_16.png)


<br><br><br>
### Selecionando todos os campos e definindo nossa operação
![Fluxo](imagens/Screenshot_17.png)

<br><br><br>
### Resultado das configurações do oData em Processing
![Fluxo](imagens/Screenshot_18.png)

<br><br><br>
### Convertendo de XML para CSV
![Fluxo](imagens/Screenshot_19.png)

<br><br><br>
### Renomenado o XML para CSV
![Fluxo](imagens/Screenshot_20.png)
```
XML To CSV Converter
```

<br><br><br>
### Configurando o XML para CSV
![Fluxo](imagens/Screenshot_21.png)
```
/Airports/Airport
```

<br><br><br>
### Adicionando o Multicast Parallel
![Fluxo](imagens/Screenshot_22.png)

<br><br><br>
### Renomeando Parallel Multicast
![Fluxo](imagens/Screenshot_23.png)
```
Parallel Multicast  
```
<br><br><br>
### Adicionando o Content Modifier
![Fluxo](imagens/Screenshot_24.png)

<br><br><br>
### Renomeando Content Modifier
![Fluxo](imagens/Screenshot_25.png)
```
Airports CSV 1 
```
<br><br><br>
### Configurando Property no Content Modifier
![Fluxo](imagens/Screenshot_26.png)
```
Content Modifier -  Airports CSV 1 
Exchange Property
Create - __filename - Contant - AirportsCSV1.csv
```
### onfigurando Body no Content Modifier
![Fluxo](imagens/Screenshot_27.png)
```
Content Modifier -  Airports CSV 1 
Message Body
Type: Expression
Body: ${property._originalPayload}
```























<br><br><br>

📂 Código e documentação

O projeto completo está disponível no GitHub:

(GitHub link aqui)
🔗 Conecte-se comigo


SAP BTP

SAP Integration Suite

APIs e integrações

Sempre aberto para trocar conhecimento com a comunidade SAP.
