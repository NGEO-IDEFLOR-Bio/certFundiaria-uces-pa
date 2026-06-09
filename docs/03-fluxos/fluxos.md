# Fluxos e Processos - IN Conjunta ITERPA / IDEFLOR-Bio

> Derivado da IN Conjunta ITERPA/IDEFLOR-Bio - Certificação Fundiária e Incorporação de Imóveis em UCES
>
> **Dica:** No GitHub, use o botão de tela cheia (fullscreen) dos diagramas Mermaid para visualização completa. Os diagramas foram desenhados de cima para baixo para evitar sobreposição com os controles de navegação.

## 1. Visão Geral do Processo

O fluxo principal e **estritamente sequencial** em 3 fases:

```mermaid
flowchart LR
    classDef iterpa fill:#D6EAF8,stroke:#2980B9,stroke-width:3px,color:#1B4F72
    classDef ideflor fill:#D5F5E3,stroke:#27AE60,stroke-width:3px,color:#1E8449
    classDef fase3 fill:#FDEBD0,stroke:#E67E22,stroke-width:3px,color:#935116
    classDef cert fill:#E8DAEF,stroke:#8E44AD,stroke-width:3px,color:#6C3483

    F1["<b>FASE I</b><br/>ITERPA<br/>Análise Fundiária"]:::iterpa
    --> |Certidão CACLG| C1(("📜 CACLG")):::cert
    --> F2["<b>FASE II</b><br/>IDEFLOR-Bio<br/>Análise e Habilitação"]:::ideflor
    --> |Certidão de Habilitação| C2(("📜 CH")):::cert
    --> F3["<b>FASE III</b><br/>ITERPA + IDEFLOR-Bio<br/>Transferência de Domínio"]:::fase3
    --> |Certidão de Conclusão| C3(("📜 CCI")):::cert

    style C1 stroke-width:4px
    style C2 stroke-width:4px
    style C3 stroke-width:4px
```

**Regra fundamental (Art. 2º, §único):** O processo somente avança à fase seguinte após a conclusão integral da fase anterior e a emissão do respectivo instrumento certificatório.

### Detalhamento das Certidões

| Certidão | Sigla | Emitida por | Habilita |
|----------|-------|-------------|----------|
| Certidão de Autenticidade, Correspondência de Localização e Localização Georreferenciada | CACLG | ITERPA | Fase II |
| Certidão de Habilitação | CH | IDEFLOR-Bio | Fase III |
| Certidão de Conclusão de Incorporação | CCI | IDEFLOR-Bio | Conclusão do processo |

---

## 2. Fluxo Detalhado - Fase I: Análise Fundiária pelo ITERPA

```mermaid
flowchart TD
    classDef iterpa fill:#D6EAF8,stroke:#2980B9,stroke-width:2px,color:#1B4F72
    classDef documento fill:#E8DAEF,stroke:#8E44AD,stroke-width:2px,color:#6C3483
    classDef decisao fill:#FFF9C4,stroke:#F1C40F,stroke-width:2px,color:#5D4037
    classDef rejeicao fill:#FADBD8,stroke:#E74C3C,stroke-width:2px,color:#922B21
    classDef inicio fill:#FFFFFF,stroke:#2C3E50,stroke-width:2px,color:#2C3E50

    REQ["🧑 Requerente<br/>Protocola requerimento<br/>físico ou eletrônico (SICARF)"]:::inicio
    --> MOD{"Indica UCES<br/>e modalidade?"}:::decisao

    MOD --> |Sim| MOD2["Indica UCES + Modalidade<br/><i>Se não: Doação Antecipada</i>"]:::iterpa
    MOD --> |Não informado| MOD2

    MOD2 --> AF["📋 Análise Formal da Documentação<br/><b>Prazo: 10 dias úteis</b>"]:::iterpa

    AF --> DOCOK{"Documentação<br/>completa?"}:::decisao

    DOCOK --> |Não| COMP["📤 Notificação para complementação<br/><b>Prazo: 30 dias corridos</b>"]:::rejeicao
    COMP --> AF

    DOCOK --> |Sim| GEO["🗺️ Análise Técnica do Georreferenciamento<br/><b>Prazo: 20 dias úteis</b><br/>Correspondência geoespacial com UCES<br/>Inexistência de óbices fundiários<br/>Necessidade de ratificação/retificação"]:::iterpa

    GEO --> PJ["⚖️ Parecer Jurídico - Procuradoria ITERPA<br/><b>Prazo: 15 dias úteis</b>"]:::iterpa

    PJ --> DP{"Decisão do<br/>Diretor-Presidente"}:::decisao

    DP --> |Aprovação| EMIT["📜 Emissão da CACLG<br/><b>Prazo: 5 dias úteis</b>"]:::documento
    DP --> |Reprovação| NAO["❌ Notificação ao requerente<br/>Possibilidade de regularização<br/>ou sobrestamento (Art. 23)"]:::rejeicao

    EMIT --> CACLG["✅ CACLG Emitida<br/>Menção: imóvel habilitado para Fase II<br/>+ Peças técnicas e jurídicas"]:::documento

    CACLG --> REMESSA["📤 Remessa do processo ao IDEFLOR-Bio"]:::iterpa

    REMESSA --> F2(("🔄 INÍCIO DA FASE II")):::inicio

    style F2 stroke:#27AE60,stroke-width:4px,color:#1E8449
    style CACLG stroke-width:3px
```

### Documentação Mínima - Fase I (Art. 8º)

1. Documentação exigida pela IN ITERPA 001/2022 para CACLG
2. Indicação da UCES de interesse
3. Indicação da modalidade de incorporação pretendida
4. Extrato atualizado do CAR no SICAR (situação ativa e regular)
5. Relatório de sobreposição com áreas protegidas, TI, TQ e imóveis públicos

---

## 3. Fluxo Detalhado - Fase II: Análise e Habilitação pelo IDEFLOR-Bio

### 3.1 Fluxo Geral - Distribuição Sequencial

```mermaid
flowchart TD
    classDef ideflor fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
    classDef documento fill:#E8DAEF,stroke:#8E44AD,stroke-width:2px,color:#6C3483
    classDef decisao fill:#FFF9C4,stroke:#F1C40F,stroke-width:2px,color:#5D4037
    classDef rejeicao fill:#FADBD8,stroke:#E74C3C,stroke-width:2px,color:#922B21
    classDef inicio fill:#FFFFFF,stroke:#2C3E50,stroke-width:2px,color:#2C3E50

    REC["📥 Recebimento do processo<br/>do ITERPA com CACLG"]:::inicio
    --> AUT["📋 Presidência: Autuação<br/>e Distribuição Interna"]:::ideflor

    AUT --> S1["1️⃣ NGEO<br/>Monitoramento Remoto<br/><b>20d úteis (+10 prorrogáveis)</b>"]:::ideflor
    S1 --> S2["2️⃣ DGMUC<br/>Análise de Pertinência<br/><b>10d úteis</b>"]:::ideflor
    S2 --> S3["3️⃣ DGB<br/>Compatibilidade Ambiental<br/><b>15d úteis</b>"]:::ideflor
    S3 --> S4["4️⃣ Procuradoria<br/>Análise Jurídica<br/><b>10d úteis</b>"]:::ideflor
    S4 --> S5["5️⃣ Presidência<br/>Deliberação Final<br/><b>5d úteis</b>"]:::ideflor

    S5 --> DELIB{"Deliberação<br/>da Presidência"}:::decisao

    DELIB --> |Deferimento<br/>com/sem condicionantes| EMITCH["📜 Emissão da CH<br/><b>5d úteis</b>"]:::documento
    DELIB --> |Indeferimento| INDEF["❌ Notificação ao requerente<br/>e ao ITERPA<br/>Recurso: 15d úteis"]:::rejeicao
    DELIB --> |Diligências complementares| DILIG["🔄 Retorno ao<br/>passo pertinente"]:::decisao

    EMITCH --> CHOK["✅ Certidão de Habilitação Emitida<br/>Validade: 2 anos (+2 prorrogável)"]:::documento

    CHOK --> F3(("🔄 INÍCIO DA FASE III")):::inicio

    style F3 stroke:#E67E22,stroke-width:4px,color:#935116
    style CHOK stroke-width:3px
```

> **Regra (Art. 11, §único):** O processo segue obrigatoriamente a ordem NGEO → DGMUC → DGB → Procuradoria → Presidência, sem pular etapas.

### 3.2 Detalhamento - NGEO (Monitoramento Remoto)

```mermaid
flowchart TD
    classDef ideflor fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
    classDef decisao fill:#FFF9C4,stroke:#F1C40F,stroke-width:2px,color:#5D4037
    classDef entrada fill:#FFFFFF,stroke:#2C3E50,stroke-width:2px,color:#2C3E50

    IN["📥 Processo recebido<br/>do ITERPA"]:::entrada
    --> NGEO["🛰️ NGEO - Monitoramento Remoto<br/><b>Prazo: 20d úteis (+10 prorrogáveis)</b>"]:::ideflor

    NGEO --> V1["✅ Confirmar localização e limites<br/>confrontando com georreferenciamento ITERPA"]:::ideflor
    --> V2["🌿 Verificar cobertura vegetal,<br/>estado de conservação, cursos d'água e nascentes"]:::ideflor
    --> V3["🏠 Identificar edificações, benfeitorias,<br/>estradas e infraestrutura"]:::ideflor
    --> V4["⚠️ Verificar passivos ambientais<br/>via sensoriamento remoto"]:::ideflor
    --> V5["🔎 Avaliar compatibilidade com<br/>os objetivos da UCES receptora"]:::ideflor

    V5 --> EXTRA{"Verificações adicionais"}:::decisao

    EXTRA --> |Requerido| PG["📊 Sobreposição com<br/>Plano de Gestão da UC"]:::ideflor
    EXTRA --> |Requerido| CF["🌲 Vocação para<br/>Compensação Florestal"]:::ideflor

    PG --> REL
    CF --> REL

    EXTRA --> |Não requerido| REL

    REL["📝 Relatório Técnico do NGEO<br/>Recomendação: SIM ou NÃO"]:::ideflor
    --> DGMUC(("➡️ Encaminha à DGMUC")):::entrada

    style DGMUC stroke:#27AE60,stroke-width:3px,color:#1E8449
```

### 3.3 Detalhamento - DGMUC (Análise de Pertinência)

```mermaid
flowchart TD
    classDef ideflor fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
    classDef decisao fill:#FFF9C4,stroke:#F1C40F,stroke-width:2px,color:#5D4037
    classDef rejeicao fill:#FADBD8,stroke:#E74C3C,stroke-width:2px,color:#922B21
    classDef alerta fill:#FFF3CD,stroke:#856404,stroke-width:2px,color:#856404
    classDef entrada fill:#FFFFFF,stroke:#2C3E50,stroke-width:2px,color:#2C3E50

    IN["📥 Relatório NGEO recebido"]:::entrada
    --> DGMUC["🏛️ DGMUC - Análise de Pertinência<br/><b>Prazo: 10d úteis</b>"]:::ideflor

    DGMUC --> A1["📍 Inserção integral ou parcial na UCES"]:::ideflor
    A1 --> A2["📋 Compatibilidade com categoria<br/>de manejo da UCES receptora"]:::ideflor
    A2 --> A3["🎯 Importância estratégica para<br/>consolidação/ampliação da UCES"]:::ideflor
    A3 --> A4["🌳 Corredores ecológicos, áreas de<br/>alta sensibilidade, remanescentes"]:::ideflor
    A4 --> A5["📐 Conformidade com o<br/>Plano de Gestão da UCES"]:::ideflor

    A5 --> RESULT{"Resultado da<br/>Nota Técnica"}:::decisao

    RESULT --> |Pertinência| DGB(("➡️ Encaminha à DGB")):::entrada
    RESULT --> |Pertinência com<br/>redirecionamento| REDIR["🔄 Consultar requerente sobre<br/>UCES alternativa<br/><b>10d úteis</b>"]:::alerta

    REDIR --> ACEITA{"Requerente<br/>aceita?"}:::decisao
    ACEITA --> |Sim| DGB
    ACEITA --> |Não| IMPERT

    RESULT --> |Impertinência| IMPERT["⚠️ Encaminha à Presidência<br/>com notificação ao requerente"]:::rejeicao

    style DGB stroke:#27AE60,stroke-width:3px,color:#1E8449
```

### 3.4 Detalhamento - DGB + Procuradoria + Presidência

```mermaid
flowchart TD
    classDef ideflor fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
    classDef documento fill:#E8DAEF,stroke:#8E44AD,stroke-width:2px,color:#6C3483
    classDef decisao fill:#FFF9C4,stroke:#F1C40F,stroke-width:2px,color:#5D4037
    classDef rejeicao fill:#FADBD8,stroke:#E74C3C,stroke-width:2px,color:#922B21
    classDef entrada fill:#FFFFFF,stroke:#2C3E50,stroke-width:2px,color:#2C3E50

    IN["📥 Nota Técnica DGMUC favorável"]:::entrada
    --> DGB["🌳 DGB - Compatibilidade Ambiental<br/><b>Prazo: 15d úteis</b>"]:::ideflor

    DGB --> D1["✅ Potencial de conservação<br/>e integridade da vegetação nativa"]:::ideflor
    D1 --> D2["🔄 Relevância para conectividade<br/>de habitats e serviços ecossistêmicos"]:::ideflor
    D2 --> D3["🔬 Pertinência para programas<br/>de conservação e pesquisa"]:::ideflor
    D3 --> D4["⚠️ Compatibilidade de passivos<br/>ambientais com objetivos da UCES"]:::ideflor
    D4 --> D5["📐 Existência de APP e RL<br/>conforme CAR"]:::ideflor

    D5 --> PARECER_DGB{"Parecer DGB"}:::decisao

    PARECER_DGB --> |Favorável| PROC
    PARECER_DGB --> |Com condicionantes| COND["📝 Condicionantes incluídas<br/>na CH e na escritura"]:::ideflor
    COND --> PROC

    PROC["⚖️ Procuradoria - Análise Jurídica<br/><b>Prazo: 10d úteis</b>"]:::ideflor
    --> P1["📋 Regularidade formal do processo"]:::ideflor
    P1 --> P2["📜 Validade e suficiência da CACLG"]:::ideflor
    P2 --> P3["🔍 Adequação da modalidade à legislação"]:::ideflor
    P3 --> P4["📝 Condicionantes e ressalvas"]:::ideflor
    P4 --> P5["🏛️ Competência do Estado para receber"]:::ideflor
    P5 --> P6["📄 Minuta de despacho<br/>de deferimento ou indeferimento"]:::ideflor

    P6 --> PRES["🏛️ Presidência - Deliberação Final<br/><b>Prazo: 5d úteis</b>"]:::ideflor

    PRES --> DELIB{"Decisão"}:::decisao

    DELIB --> |✅ Deferir<br/>com/sem condicionantes| EMIT["📜 Emissão da CH<br/><b>5d úteis</b>"]:::documento
    DELIB --> |❌ Indeferir<br/>fundamentadamente| INDEF["❌ Notificação ao requerente<br/>e ao ITERPA"]:::rejeicao
    DELIB --> |🔄 Diligências<br/>complementares| DILIG["Retorno ao<br/>passo pertinente"]:::decisao

    EMIT --> CHOK["✅ CERTIDÃO DE HABILITAÇÃO<br/>Validade: 2 anos (+2 prorrogável)<br/>Condição necessária para Fase III"]:::documento

    INDEF --> REC["📝 Recurso Administrativo<br/><b>15d úteis</b><br/>Efeito suspensivo (regra)<br/>Decisões compartilhadas: ITERPA + IDEFLOR"]:::rejeicao

    style CHOK stroke-width:3px
    style DILIG stroke:#E67E22,stroke-width:2px
```

### Conteúdo Obrigatório da CH (Art. 16)

| Campo | Descrição |
|-------|-----------|
| I | Identificação completa do imóvel (matrícula, município, coordenadas, área em ha) |
| II | Referência à CACLG (número e data) |
| III | Identificação do Doador ou Doador Beneficiário |
| IV | UCES receptora, categoria de manejo e zona de inserção |
| V | Área habilitada em hectares (quando diferente da área total) |
| VI | Modalidade de incorporação |
| VII | Condicionantes técnicas ou ambientais para Fase III |
| VIII | Prazo de validade: 2 anos (prorrogáveis por +2 anos) |
| IX | Declaração de que a CH é condição necessária para Fase III |

---

## 4. Fluxo Detalhado - Fase III: Transferência do Domínio

```mermaid
flowchart TD
    classDef fase3 fill:#FDEBD0,stroke:#E67E22,stroke-width:2px,color:#935116
    classDef documento fill:#E8DAEF,stroke:#8E44AD,stroke-width:2px,color:#6C3483
    classDef inicio fill:#FFFFFF,stroke:#2C3E50,stroke-width:2px,color:#2C3E50
    classDef iterpa fill:#D6EAF8,stroke:#2980B9,stroke-width:2px,color:#1B4F72
    classDef ideflor fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449

    CHOK["✅ CH Emitida"]:::inicio
    --> REQ["🧑 Requerimento do Doador<br/>ao IDEFLOR-Bio solicitando<br/>lavratura da escritura"]:::ideflor

    REQ --> ENC["📤 IDEFLOR-Bio encaminha<br/>ao ITERPA"]:::ideflor

    ENC --> VERIF["📋 ITERPA: Verificação de Documentos<br/>Solicitar atualização dos vencidos"]:::iterpa

    VERIF --> MINUTA["📄 ITERPA: Elaboração de Minuta de Escritura<br/><b>Prazo: 15d úteis</b><br/>Cláusulas obrigatórias (Art. 20)"]:::iterpa

    MINUTA --> CLAUSULAS["📝 Cláusulas da Escritura"]:::fase3

    CLAUSULAS --> C1["I - Qualificação das partes"]:::fase3
    C1 --> C2["II - Descrição do imóvel conforme geo"]:::fase3
    C2 --> C3["III - Livre e desembaraçado"]:::fase3
    C3 --> C4["IV - Aceite do Estado do Pará (ITERPA)"]:::fase3
    C4 --> C5["V - Destinação à UCES sob gestão IDEFLOR-Bio"]:::fase3
    C5 --> C6["VI - Modalidade + créditos de compensação"]:::fase3
    C6 --> C7["VII - Condicionantes da CH"]:::fase3
    C7 --> C8["VIII - Ocupações tradicionais (Termo de Acordo)"]:::fase3

    C8 --> LAV["📝 Lavratura da Escritura<br/>Cartório de Notas competente<br/><b>Despesas: Doador (regra geral)</b>"]:::fase3

    LAV --> REG["📋 Registro no Cartório de Imóveis<br/><b>Prazo: 30 dias corridos</b>"]:::fase3

    REG --> COM["📤 ITERPA comunica IDEFLOR-Bio<br/>Inc. ao patrimônio do Estado<br/>+ Atualização do CNUC"]:::iterpa

    COM --> CCI["📜 Certidão de Conclusão de Incorporação<br/><b>Prazo: 10d úteis</b><br/>Matrícula + Área + UCES + Modalidade + Créditos"]:::documento

    CCI --> FIM(("✅ PROCESSO CONCLUÍDO")):::inicio

    style FIM stroke:#27AE60,stroke-width:4px,color:#1E8449
    style CCI stroke-width:3px
    style CHOK stroke:#8E44AD,stroke-width:3px
```

---

## 5. Fluxo de Recursos Administrativos

```mermaid
flowchart TD
    classDef decisao fill:#FFF9C4,stroke:#F1C40F,stroke-width:2px,color:#5D4037
    classDef rejeicao fill:#FADBD8,stroke:#E74C3C,stroke-width:2px,color:#922B21
    classDef iterpa fill:#D6EAF8,stroke:#2980B9,stroke-width:2px,color:#1B4F72
    classDef ideflor fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
    classDef entrada fill:#FFFFFF,stroke:#2C3E50,stroke-width:2px,color:#2C3E50

    INDEF["❌ Indeferimento<br/>Fase I ou Fase II"]:::rejeicao
    --> REC["📝 Recurso Administrativo<br/><b>Prazo: 15d úteis</b>"]:::entrada

    REC --> DIR["🏛️ Diretor-Presidente<br/>do órgão responsável"]:::decisao

    DIR --> EFEITO["⚠️ Efeito suspensivo<br/><i>Regra geral</i><br/>Salvo decisão em contrário<br/>no interesse público"]:::decisao

    EFEITO --> COMP{"Competências<br/>compartilhadas?"}:::decisao

    COMP --> |Sim| CONJ["🏛️ Decisão Conjunta<br/>Diretores-Presidentes<br/>ITERPA + IDEFLOR-Bio<br/><i>Art. 28, §2º</i>"]:::iterpa
    COMP --> |Não| UNI["🏛️ Decisão Unilateral<br/>do Diretor-Presidente<br/>do órgão responsável"]:::ideflor

    CONJ --> RESULT{"Resultado"}:::decisao
    UNI --> RESULT

    RESULT --> |Deferimento| PROSSEGUIR["✅ Prosseguimento<br/>do processo"]:::ideflor
    RESULT --> |Indeferimento| ARQUIVAR["📁 Arquivamento<br/>do processo"]:::rejeicao

    style INDEF stroke-width:2px
```

---

## 6. Fluxo de Gestão de Créditos de Compensação

```mermaid
flowchart TD
    classDef ideflor fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
    classDef documento fill:#E8DAEF,stroke:#8E44AD,stroke-width:2px,color:#1E8449
    classDef entrada fill:#FFFFFF,stroke:#2C3E50,stroke-width:2px,color:#2C3E50

    CCI["📜 Certidão de Conclusão<br/>de Incorporação"]:::documento
    --> REG["📝 Registro no Sistema de Créditos<br/>do IDEFLOR-Bio"]:::ideflor

    REG --> DADOS["📋 Dados Registrados"]:::ideflor

    DADOS --> D1["👤 Identificação do Doador Beneficiário"]:::ideflor
    D1 --> D2["🏠 Imóvel incorporado<br/>matrícula + área em ha"]:::ideflor
    D2 --> D3["🔄 Modalidade de compensação"]:::ideflor
    D3 --> D4["📊 Crédito disponível em hectares"]:::ideflor
    D4 --> D5["📜 Histórico de utilização"]:::ideflor
    D5 --> D6["📅 Data de vencimento<br/><i>se aplicável</i>"]:::ideflor

    D6 --> UTIL["🔄 Utilização de Créditos"]:::ideflor

    UTIL --> U1["🏛️ SEMAS<br/>Regularização ambiental"]:::ideflor
    UTIL --> U2["🏛️ ITERPA<br/>Regularização fundiária<br/>com contrapartida ambiental"]:::ideflor
    UTIL --> U3["🏛️ Outros órgãos competentes<br/>Legislação aplicável"]:::ideflor

    U1 --> RED["📉 Redução imediata<br/>do saldo disponível"]:::ideflor
    U2 --> RED
    U3 --> RED

    RED --> CERT["📜 Certidão Individualizada<br/>de Créditos Disponíveis<br/><i>Quando solicitada</i>"]:::documento

    style CCI stroke-width:3px
    style RED stroke:#E74C3C,stroke-width:2px
    style CERT stroke-width:3px
```

---

## 7. Impedimentos à Incorporação (Art. 6º)

```mermaid
flowchart LR
    classDef bloqueio fill:#FADBD8,stroke:#C0392B,stroke-width:2px,color:#922B21
    classDef exececao fill:#FEF9E7,stroke:#F4D03F,stroke-width:2px,color:#7D6608
    classDef check fill:#D6EAF8,stroke:#2980B9,stroke-width:2px,color:#1B4F72

    IMOVEL["🏠 Imóvel Rural"]:::check
    --> V1{"Pendências na<br/>cadeia dominial?"}:::check
    IMOVEL --> V2{"Litígio judicial<br/>ou administrativo?"}:::check
    IMOVEL --> V3{"Passivos ambientais<br/>consolidados?"}:::check
    IMOVEL --> V4{"Sobreposição com<br/>propriedades certificadas<br/>ou áreas de comunidades?"}:::check
    IMOVEL --> V5{"CAR inativo<br/>ou irregular?"}:::check
    IMOVEL --> V6{"Área inferior ao<br/>módulo fiscal?"}:::check
    IMOVEL --> V7{"Edificações incompatíveis<br/>com UCES?"}:::check

    V1 --> |Sim| B1["🚫 VEDADO<br/><b>Salvo sentença<br/>transitada em julgado</b>"]:::bloqueio
    V2 --> |Sim| B2["🚫 VEDADO<br/><b>Salvo decisão<br/>administrativa definitiva</b>"]:::bloqueio
    V3 --> |Sim| B3["🚫 VEDADO<br/>Incompatível com<br/>objetivos da UCES"]:::bloqueio
    V4 --> |Sim| B4["🚫 VEDADO"]:::bloqueio
    V5 --> |Sim| B5["🚫 VEDADO<br/>CAR deve estar ativo<br/>e regular no SICAR"]:::bloqueio
    V6 --> |Sim| E1["⚠️ VEDADO<br/><b>Salvo complementação<br/>de perímetro de UCES</b>"]:::exececao
    V7 --> |Sim| E2["⚠️ VEDADO<br/><b>Salvo plano de adequação<br/>aprovado pelo IDEFLOR-Bio</b>"]:::exececao

    V1 --> |Não| OK1["✅"]:::check
    V2 --> |Não| OK2["✅"]:::check
    V3 --> |Não| OK3["✅"]:::check
    V4 --> |Não| OK4["✅"]:::check
    V5 --> |Não| OK5["✅"]:::check
    V6 --> |Não| OK6["✅"]:::check
    V7 --> |Não| OK7["✅"]:::check

    style B1 stroke-width:2px
    style B2 stroke-width:2px
    style B3 stroke-width:2px
    style B4 stroke-width:2px
    style B5 stroke-width:2px
    style E1 stroke-width:2px
    style E2 stroke-width:2px
```

> **Nota sobre ocupações tradicionais (Art. 6º, §2º):** A existência de ocupações tradicionais no imóvel **não constitui impedimento**, desde que compatíveis com os objetivos da UCES e sujeitas a Termo de Acordo entre IDEFLOR-Bio e os ocupantes.

---

## 8. Quadro Resumo de Prazos

### Fase I - ITERPA

| Etapa | Prazo | Referência |
|-------|-------|------------|
| Análise formal da documentação | 10 dias úteis | Art. 38, I |
| Complementação de documentos (requerente) | 30 dias corridos | Art. 38, II |
| Análise técnica do georreferenciamento | 20 dias úteis | Art. 38, III |
| Parecer jurídico ITERPA | 15 dias úteis | Art. 38, IV |
| Emissão da CACLG | 5 dias úteis | Art. 38, V |

### Fase II - IDEFLOR-Bio

| Etapa | Prazo | Referência |
|-------|-------|------------|
| Análise de pertinência (DGMUC) | 10 dias úteis | Art. 39, I |
| Checagem/monitoramento remoto (NGEO) | 20 dias úteis (+10) | Art. 39, II |
| Análise compatibilidade ambiental (DGB) | 15 dias úteis | Art. 39, III |
| Parecer jurídico (Procuradoria) | 10 dias úteis | Art. 39, IV |
| Deliberação da Presidência | 5 dias úteis | Art. 39, V |
| Emissão da CH | 5 dias úteis | Art. 39, VI |
| Consulta sobre redirecionamento (requerente) | 10 dias úteis | Art. 13, §3º |
| Recurso administrativo | 15 dias úteis | Art. 28 |

### Fase III - Transferência

| Etapa | Prazo | Referência |
|-------|-------|------------|
| Elaboração de minuta de escritura (ITERPA) | 15 dias úteis | Art. 40, I |
| Registro da escritura (ITERPA) | 30 dias corridos | Art. 40, II |
| Emissão Certidão de Conclusão (IDEFLOR-Bio) | 10 dias úteis | Art. 40, III |
| Validade da CH | 2 anos (+2 anos prorrogável) | Art. 16, VIII |

### Linha do Tempo Visual

```mermaid
gantt
    title Prazos por Fase (estimativa melhor cenário)
    dateFormat  X
    axisFormat  %s

    section Fase I - ITERPA
    Análise Formal              :0, 10
    Georreferenciamento         :10, 30
    Parecer Jurídico            :30, 45
    Emissão CACLG               :45, 50

    section Fase II - IDEFLOR-Bio
    DGMUC - Pertinência         :50, 60
    NGEO - Monitoramento        :60, 80
    DGB - Compatibilidade       :80, 95
    Procuradoria                :95, 105
    Presidência                 :105, 110
    Emissão CH                  :110, 115

    section Fase III - Transferência
    Minuta de Escritura         :115, 130
    Registro Escritura (30d)    :130, 160
    Certidão de Conclusão       :160, 170
```

> **Total estimado:** ~50 dias úteis (Fase I) + ~65 dias úteis (Fase II) + ~55 dias corridos (Fase III) = **aproximadamente 14-16 semanas** no melhor cenário, sem pendências ou prorrogações.