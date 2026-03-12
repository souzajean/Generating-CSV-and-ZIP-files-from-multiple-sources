# 🚀 Generating CSV and ZIP Files from Multiple Sources
### SAP BTP Integration Suite (CPI)

Projeto de laboratório desenvolvido durante meus estudos em **SAP BTP – Integration Suite (Cloud Integration)**.

O objetivo deste projeto é demonstrar como construir um **iFlow capaz de consumir dados de múltiplas fontes, converter os dados em CSV e gerar um arquivo ZIP contendo múltiplos arquivos**.

Esse tipo de cenário é comum em **integrações empresariais**, quando precisamos consolidar dados provenientes de diferentes sistemas e gerar arquivos para parceiros externos ou sistemas legados.

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
📤 Resultado gerado pela integração

A integração gera dois arquivos CSV e os compacta automaticamente em um arquivo ZIP.

doc.zip
 ├── doc1.csv  (dados do Postman)
 └── doc2.csv  (dados da API TripPin)

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





📂 Código e documentação

O projeto completo está disponível no GitHub:

(GitHub link aqui)
🔗 Conecte-se comigo


SAP BTP

SAP Integration Suite

APIs e integrações

Sempre aberto para trocar conhecimento com a comunidade SAP.
