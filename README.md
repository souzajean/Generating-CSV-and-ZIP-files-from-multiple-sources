# Generating-CSV-and-ZIP-files-from-multiple-sources
SAP BTP CPI - Zipping Multiple Files



🚀 SAP Integration Suite (CPI) – Gerando arquivos CSV e ZIP a partir de múltiplas fontes

Durante meus estudos em SAP BTP – Integration Suite (Cloud Integration), desenvolvi um pequeno laboratório para praticar alguns conceitos importantes de integração.

O objetivo deste exercício foi construir um iFlow capaz de consumir dados de duas fontes diferentes, converter os dados em CSV e gerar um arquivo ZIP com múltiplos arquivos.

Esse tipo de cenário é comum em projetos reais quando precisamos consolidar dados de diferentes sistemas e gerar arquivos para integração com parceiros ou sistemas legados.

🧩 Cenário da Integração

A integração possui duas fontes de dados:

1️⃣ Payload enviado via Postman (XML)
2️⃣ Dados consumidos de uma API OData pública

API utilizada:

https://services.odata.org/V4/TripPinServiceRW/Airports

Essa API retorna informações sobre aeroportos.

🏗 Arquitetura do iFlow

O fluxo foi desenvolvido utilizando SAP Integration Suite – Cloud Integration (CPI).

Fluxo da integração:

Client (Postman)
      │
      ▼
HTTPS Sender
      │
      ▼
Content Modifier
(Save original payload)
      │
      ▼
Request Reply
(OData API - TripPin Airports)
      │
      ▼
Parallel Multicast
      │
      ├── Branch 1
      │      Restore original payload
      │      Convert XML → CSV
      │      File: doc1.csv
      │
      └── Branch 2
             Convert API Response → CSV
             File: doc2.csv

      ▼
Join
      ▼
Gather (Zip Aggregation)
      ▼
SFTP Receiver

Resultado final:

doc.zip
 ├── doc1.csv
 └── doc2.csv
🔧 Tecnologias Utilizadas

Nesse laboratório utilizei alguns componentes importantes do SAP CPI:

HTTPS Sender Adapter

Content Modifier

Request Reply

OData API

Parallel Multicast

XML to CSV Converter

Join

Gather (ZIP Aggregation)

SFTP Receiver

Esses componentes são muito utilizados em projetos reais de integração.

📥 Exemplo do Payload enviado via Postman
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

💡 Próximos passos

Continuarei desenvolvendo novos cenários de integração utilizando:

SAP Event Mesh

APIs REST

Processamento de arquivos

Groovy Scripts

Integrações com sistemas externos

📂 Código e documentação

O projeto completo está disponível no GitHub:

(GitHub link aqui)
🔗 Conecte-se comigo

Sou Consultor de Infraestrutura SAP Business One e atualmente estou aprofundando meus estudos em:

SAP BTP

SAP Integration Suite

APIs e integrações

Sempre aberto para trocar conhecimento com a comunidade SAP.
