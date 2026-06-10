# Modelo de Dados Conceitual - IN Conjunta ITERPA / IDEFLOR-Bio

> Derivado da IN Conjunta ITERPA/IDEFLOR-Bio - Certificação Fundiária e Incorporação de Imóveis em UCES
>
> **Dica:** No GitHub, use o botão de tela cheia (fullscreen) dos diagramas Mermaid para visualização completa.

## 1. Visão Geral - Relacionamentos

```mermaid
erDiagram
    REQUERENTE ||--o{ IMOVEL_RURAL : possui
    UCES ||--o{ IMOVEL_RURAL : contem
    REQUERENTE ||--o{ PROCESSO : requere
    IMOVEL_RURAL ||--o{ PROCESSO : objeto_de
    MODALIDADE ||--o{ PROCESSO : tipo_de
    PROCESSO ||--|| CACLG : gera
    CACLG ||--|| CERTIDAO_HABILITACAO : habilita
    CERTIDAO_HABILITACAO ||--|| ESCRITURA : origina
    ESCRITURA ||--|| CERTIDAO_CONCLUSAO : finaliza
    PROCESSO ||--o{ PARECER : possui
    CERTIDAO_CONCLUSAO ||--o| CREDITO : gera
    CREDITO ||--o{ UTILIZACAO : possui
    PROCESSO ||--o{ PRAZO : controla
    PROCESSO ||--o{ LOG_EVENTO : registra
```

---

## 2. Entidades Principais - Processo e Atores

```mermaid
classDiagram
    class PROCESSO {
        +id_processo: PK
        +numero_processo: string
        +data_protocolo: date
        +tipo_requerimento: string
        +fase_atual: string
        +status_processo: string
        +vinculacao_compensacao: boolean
        +data_criacao: datetime
        +data_atualizacao: datetime
    }

    class REQUERENTE {
        +id_requerente: PK
        +tipo_pessoa: string
        +cpf_cnpj: string
        +nome_razao_social: string
        +qualificacao: string
        +email: string
    }

    class MODALIDADE {
        +id_modalidade: PK
        +codigo: string
        +nome: string
        +gera_credito: boolean
    }

    PROCESSO --> REQUERENTE
    PROCESSO --> MODALIDADE

    style PROCESSO fill:#D6EAF8,stroke:#2980B9,stroke-width:3px,color:#1B4F72
    style REQUERENTE fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
    style MODALIDADE fill:#FFF9C4,stroke:#F1C40F,stroke-width:2px,color:#5D4037
```

---

## 3. Entidades Principais - Imóvel e UCES

```mermaid
classDiagram
    class IMOVEL_RURAL {
        +id_imovel: PK
        +numero_matricula: string
        +municipio: string
        +uf: string
        +coordenadas_geograficas: GeoJSON
        +area_total_ha: decimal
        +area_habilitada_ha: decimal
        +car_numero: string
        +car_status: string
        +bioma: string
        +modulo_fiscal_municipio: decimal
        +possui_ocupacoes_tradicionais: boolean
        +possui_benfeitorias: boolean
    }

    class UCES {
        +id_uces: PK
        +nome: string
        +categoria_manejo: string
        +zona_insercao: string
        +bioma: string
        +municipio: string
        +area_total_ha: decimal
        +plano_gestao_existente: boolean
        +limites_geograficos: GeoJSON
        +codigo_cnuc: string
    }

    IMOVEL_RURAL --> UCES

    style IMOVEL_RURAL fill:#FDEBD0,stroke:#E67E22,stroke-width:3px,color:#935116
    style UCES fill:#E8DAEF,stroke:#8E44AD,stroke-width:3px,color:#6C3483
```

---

## 4. Entidades de Certificação - CACLG (Fase I)

```mermaid
classDiagram
    class CACLG {
        +id_caclg: PK
        +numero_caclg: string
        +data_emissao: date
        +data_validade: date
        +status: string
        +cadeia_dominial_regular: boolean
        +georreferenciamento_valido: boolean
        +correspondencia_localizacao: boolean
        +habilitado_fase_ii: boolean
        +observacoes_iterpa: text
        +documento_caclg: arquivo
        +pecas_tecnicas_juridicas: arquivo[]
    }

    style CACLG fill:#D6EAF8,stroke:#2980B9,stroke-width:3px,color:#1B4F72
```

---

## 5. Entidades de Certificação - CH (Fase II)

```mermaid
classDiagram
    class CERTIDAO_HABILITACAO {
        +id_ch: PK
        +numero_ch: string
        +data_emissao: date
        +data_validade: date
        +status: string
        +area_habilitada_ha: decimal
        +condicionantes_tecnicas_ambientais: text
        +condicao_necessaria_fase_iii: boolean
        +documento_ch: arquivo
    }

    style CERTIDAO_HABILITACAO fill:#D5F5E3,stroke:#27AE60,stroke-width:3px,color:#1E8449
```

---

## 6. Entidades de Certificação - Escritura e Conclusão (Fase III)

```mermaid
classDiagram
    class ESCRITURA {
        +id_escritura: PK
        +numero_escritura: string
        +data_lavratura: date
        +cartorio_notas: string
        +qualificacao_partes: text
        +descricao_imovel_geo: text
        +declaracao_livre_desembaracado: text
        +aceite_estado_para: boolean
        +clausula_destinacao_uces: text
        +modalidade_doacao: string
        +creditos_compensacao_gerados: decimal
        +condicionantes_ch: text
        +clausula_ocupacoes_tradicionais: text
        +despesas_responsavel: string
        +data_registro: date
        +status: string
        +arquivo_escritura: arquivo
    }

    class CERTIDAO_CONCLUSAO {
        +id_certidao_conclusao: PK
        +numero_certidao: string
        +data_emissao: date
        +numero_matricula_nova: string
        +area_incorporada_ha: decimal
        +creditos_compensacao_gerados_ha: decimal
        +data_registro: date
        +documento_certidao: arquivo
    }

    ESCRITURA --> CERTIDAO_CONCLUSAO

    style ESCRITURA fill:#FDEBD0,stroke:#E67E22,stroke-width:3px,color:#935116
    style CERTIDAO_CONCLUSAO fill:#E8DAEF,stroke:#8E44AD,stroke-width:3px,color:#6C3483
```

---

## 7. Entidades de Análise - Parecer

```mermaid
classDiagram
    class PARECER {
        +id_parecer: PK
        +unidade_emitente: string
        +tipo_parecer: string
        +data_inicio: date
        +data_conclusao: date
        +prazo_dias_uteis: int
        +resultado: string
        +conteudo: text
        +condicionantes: text
        +responsavel: string
        +arquivo_parecer: arquivo
    }

    style PARECER fill:#FFF9C4,stroke:#F1C40F,stroke-width:3px,color:#5D4037
```

---

## 8. Entidades de Análise - NGEO

```mermaid
classDiagram
    class ANALISE_NGEO {
        +id_analise_ngeo: PK
        +localizacao_confirmada: boolean
        +limites_confrontados_geo: boolean
        +cobertura_vegetal: text
        +estado_conservacao: text
        +passivos_ambientais_remoto: boolean
        +compatibilidade_uces: boolean
        +sobreposicao_plano_gestao: boolean
        +vocacao_compensacao_florestal: boolean
        +recomendacao_recebimento: boolean
        +necessidade_visitoria_campo: boolean
    }

    style ANALISE_NGEO fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
```

---

## 9. Entidades de Análise - DGMUC e DGB

```mermaid
classDiagram
    class ANALISE_DGMUC {
        +id_analise_dgmuc: PK
        +imovel_inserido_integralmente: boolean
        +imovel_inserido_parcialmente: boolean
        +compatibilidade_categoria_manejo: boolean
        +importancia_estrategica: text
        +corredores_ecologicos: boolean
        +conformidade_plano_gestao: boolean
        +resultado: string
    }

    class ANALISE_DGB {
        +id_analise_dgb: PK
        +potencial_conservacao: text
        +integridade_ecossistemas: text
        +passivos_ambientais_recuperaveis: boolean
        +areas_app: boolean
        +areas_rl: boolean
        +compatibilidade_ambiental: boolean
        +condicionantes_incorporacao: text
    }

    ANALISE_DGMUC --> UCES : uces_alternativa_sugerida

    class UCES {
        +id_uces: PK
        +nome: string
    }

    style ANALISE_DGMUC fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
    style ANALISE_DGB fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
    style UCES fill:#E8DAEF,stroke:#8E44AD,stroke-width:2px,color:#6C3483
```

---

## 10. Entidades de Análise - Procuradoria

```mermaid
classDiagram
    class ANALISE_JURIDICA_IDEFLOR {
        +id_analise_juridica: PK
        +regularidade_formal: boolean
        +validade_caclg: boolean
        +suficiencia_caclg: boolean
        +adequacao_modalidade: boolean
        +condicionantes_legais: text
        +competencia_estado: boolean
        +tipo_despacho: string
        +irregularidades_sanaveis: text
    }

    style ANALISE_JURIDICA_IDEFLOR fill:#D5F5E3,stroke:#27AE60,stroke-width:2px,color:#1E8449
```

---

## 11. Entidades de Créditos de Compensação

```mermaid
classDiagram
    class CREDITO {
        +id_credito: PK
        +credito_disponivel_ha: decimal
        +credito_utilizado_ha: decimal
        +saldo_disponivel_ha: decimal
        +data_vencimento: date
        +status: string
    }

    class UTILIZACAO {
        +id_utilizacao: PK
        +data_utilizacao: date
        +orgao_destino: string
        +hectares_utilizados: decimal
        +descricao: text
    }

    CREDITO --> UTILIZACAO

    style CREDITO fill:#E8DAEF,stroke:#8E44AD,stroke-width:3px,color:#6C3483
    style UTILIZACAO fill:#D7BDE2,stroke:#8E44AD,stroke-width:2px,color:#6C3483
```

---

## 12. Entidades de Controle - Prazos e Logs

```mermaid
classDiagram
    class PRAZO {
        +id_prazo: PK
        +fase: string
        +etapa: string
        +data_inicio: datetime
        +prazo_dias: int
        +tipo_prazo: string
        +data_limite: datetime
        +data_conclusao: datetime
        +prorrogado: boolean
        +status: string
    }

    class LOG_EVENTO {
        +id_log: PK
        +data_hora: datetime
        +acao: string
        +unidade_responsavel: string
        +usuario_responsavel: string
        +observacoes: text
    }

    style PRAZO fill:#D6EAF8,stroke:#2980B9,stroke-width:2px,color:#1B4F72
    style LOG_EVENTO fill:#D6EAF8,stroke:#2980B9,stroke-width:2px,color:#1B4F72
```

---

## 13. Diagrama do Fluxo de Certidões

```mermaid
flowchart TD
    classDef iterpa fill:#D6EAF8,stroke:#2980B9,stroke-width:3px,color:#1B4F72
    classDef ideflor fill:#D5F5E3,stroke:#27AE60,stroke-width:3px,color:#1E8449
    classDef fase3 fill:#FDEBD0,stroke:#E67E22,stroke-width:3px,color:#935116
    classDef cert fill:#E8DAEF,stroke:#8E44AD,stroke-width:3px,color:#6C3483
    classDef processo fill:#FFF9C4,stroke:#F1C40F,stroke-width:2px,color:#5D4037

    PROC["PROCESSO"]:::processo

    PROC --> CACLG["CACLG<br/>Fase I - ITERPA<br/><b>Certidão de Autenticidade</b><br/>Cadeia Dominial + Geo"]:::iterpa
    CACLG --> CH["CH<br/>Fase II - IDEFLOR-Bio<br/><b>Certidão de Habilitação</b><br/>Pertinência + Compatibilidade"]:::ideflor
    CH --> ESCR["ESCRITURA<br/>Fase III<br/><b>Doação Registrada</b><br/>Transferência de Domínio"]:::fase3
    ESCR --> CCI["CCI<br/>Fase III<br/><b>Certidão de Conclusão</b><br/>Incorporação ao Patrimônio"]:::cert

    CCI --> CRED["CRÉDITOS DE<br/>COMPENSAÇÃO<br/>ha disponíveis"]:::cert

    style CACLG stroke-width:4px
    style CH stroke-width:4px
    style ESCR stroke-width:4px
    style CCI stroke-width:4px
    style CRED stroke-width:3px
```

---

## 14. Diagrama de Estados do Processo

```mermaid
stateDiagram-v2
    [*] --> requerido

    state "FASE I - ITERPA" as faseI {
        requerido --> em_analise_formal
        em_analise_formal --> em_analise_georreferenciamento : Documentacao OK
        em_analise_georreferenciamento --> em_parecer_juridico_iterpa
        em_parecer_juridico_iterpa --> caclg_emitida : Aprovacao
    }

    state "FASE II - IDEFLOR-Bio" as faseII {
        caclg_emitida --> em_analise_ngeo
        em_analise_ngeo --> em_analise_dgmuc
        em_analise_dgmuc --> em_analise_dgb : Pertinencia
        em_analise_dgb --> em_analise_juridica_ideflor
        em_analise_juridica_ideflor --> em_deliberacao_presidencia
        em_deliberacao_presidencia --> ch_emitida : Deferimento
    }

    state "FASE III - Transferencia" as faseIII {
        ch_emitida --> em_elaboracao_minuta
        em_elaboracao_minuta --> escritura_lavrada
        escritura_lavrada --> escritura_registrada
        escritura_registrada --> concluido
    }

    em_parecer_juridico_iterpa --> indeferido : Reprovacao
    em_deliberacao_presidencia --> indeferido : Indeferimento
    em_deliberacao_presidencia --> requerido : Diligencias

    concluido --> [*]
    indeferido --> [*]
```

---

## 15. Enums / Domínios

### MODALIDADE_INCORPORACAO

| Valor | Descrição |
|-------|-----------|
| `doacao_voluntaria` | Doação voluntária |
| `doacao_antecipada` | Doação antecipada |
| `compensacao_reserva_legal` | Compensação de Reserva Legal |
| `compensacao_florestal` | Compensação florestal |
| `medidas_compensatorias_ambientais` | Cumprimento de medidas compensatórias ambientais |

### FASE_PROCESSO

| Valor | Descrição |
|-------|-----------|
| `I` | Fase I - Análise Fundiária (ITERPA) |
| `II` | Fase II - Análise e Habilitação (IDEFLOR-Bio) |
| `III` | Fase III - Transferência de Domínio |

### STATUS_PROCESSO

| Valor | Fase | Descrição |
|-------|------|-----------|
| `requerido` | I | Processo protocolado |
| `em_analise_formal` | I | Análise formal da documentação |
| `em_analise_georreferenciamento` | I | Análise técnica do georreferenciamento |
| `em_parecer_juridico_iterpa` | I | Parecer jurídico ITERPA |
| `caclg_emitida` | I→II | CACLG emitida, aguardando remessa |
| `em_analise_ngeo` | II | Análise no NGEO |
| `em_analise_dgmuc` | II | Análise de pertinência na DGMUC |
| `em_analise_dgb` | II | Análise de compatibilidade na DGB |
| `em_analise_juridica_ideflor` | II | Parecer jurídico IDEFLOR-Bio |
| `em_deliberacao_presidencia` | II | Deliberação da Presidência |
| `ch_emitida` | II→III | CH emitida |
| `em_elaboracao_minuta` | III | Elaboração de minuta de escritura |
| `escritura_lavrada` | III | Escritura lavrada |
| `escritura_registrada` | III | Escritura registrada |
| `concluido` | III | Processo concluído |
| `indeferido` | - | Processo indeferido |
| `arquivado` | - | Processo arquivado |

### TIPO_PARECER

| Valor | Descrição |
|-------|-----------|
| `tecnico` | Parecer técnico |
| `juridico` | Parecer jurídico |
| `nota_tecnica` | Nota técnica |
| `despacho` | Despacho |

### RESULTADO_PARECER

| Valor | Descrição |
|-------|-----------|
| `favoravel` | Favorável |
| `favoravel_com_ressalvas` | Favorável com ressalvas |
| `desfavoravel` | Desfavorável |
| `diligencia` | Determinação de diligências complementares |

### RESULTADO_DGMUC

| Valor | Descrição |
|-------|-----------|
| `pertinencia` | Pertinência da incorporação |
| `pertinencia_redirecionamento` | Pertinência com redirecionamento a outra UCES |
| `impertinencia` | Impertinência da incorporação |

### STATUS_CACLG

| Valor | Descrição |
|-------|-----------|
| `em_analise` | Em análise pelo ITERPA |
| `emitida` | CACLG emitida |
| `vencida` | CACLG vencida |
| `cancelada` | CACLG cancelada |

### STATUS_CH

| Valor | Descrição |
|-------|-----------|
| `em_analise` | Em análise pelo IDEFLOR-Bio |
| `emitida` | CH emitida |
| `vencida` | CH vencida |
| `prorrogada` | CH prorrogada |
| `cancelada` | CH cancelada |

### STATUS_ESCRITURA

| Valor | Descrição |
|-------|-----------|
| `minuta` | Minuta elaborada |
| `lavrada` | Escritura lavrada |
| `registrada` | Escritura registrada |

### CAR_STATUS

| Valor | Descrição |
|-------|-----------|
| `ativo` | CAR ativo e regular no SICAR |
| `irregular` | CAR irregular |
| `inexistente` | CAR inexistente |

### TIPO_PESSOA

| Valor | Descrição |
|-------|-----------|
| `fisica` | Pessoa física |
| `juridica` | Pessoa jurídica |

### QUALIFICACAO_DOADOR

| Valor | Descrição |
|-------|-----------|
| `doador` | Doador |
| `beneficiario` | Beneficiário |
| `doador_beneficiario` | Doador Beneficiário |