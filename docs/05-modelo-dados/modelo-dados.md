# Modelo de Dados Conceitual - IN Conjunta ITERPA / IDEFLOR-Bio

> Derivado da IN Conjunta ITERPA/IDEFLOR-Bio - Certificação Fundiária e Incorporação de Imóveis em UCES

## 1. Entidades Principais

### 1.1 Processo

```
PROCESSO
├── id_processo (PK)
├── numero_processo
├── data_protocolo
├── tipo_requerimento (fisico | eletronico)
├── uces_indicada (FK → UCES)
├── modalidade_incorporacao (FK → MODALIDADE)
├── vinculacao_compensacao (booleano)
├── processo_compensacao_vinculado (opcional)
├── fase_atual (I | II | III)
├── status_processo
├── data_criacao
├── data_atualizacao
└── requerente (FK → REQUERENTE)
```

### 1.2 Requerente / Doador

```
REQUERENTE
├── id_requerente (PK)
├── tipo_pessoa (fisica | juridica)
├── cpf_cnpj
├── nome_razao_social
├── endereco
├── telefone
├── email
├── qualificacao (doador | beneficiario | doador_beneficiario)
└── representante_legal (quando PJ)
```

### 1.3 Imóvel Rural

```
IMOVEL_RURAL
├── id_imovel (PK)
├── numero_matricula
├── cartorio_registro
├── municipio
├── uf
├── coordenadas_geograficas (GeoJSON)
├── area_total_ha
├── area_habilitada_ha
├── car_numero
├── car_status (ativo | irregular | inexistente)
├── codigo_sicar
├── uces (FK → UCES)
├── doador (FK → REQUERENTE)
├── modulo_fiscal_municipio
├── area_modulo_fiscal
├── bioma
├── possui_ocupacoes_tradicionais
├── possui_benfeitorias
├── possui_edificacoes
└── tipo_imovel (doador | outro)
```

### 1.4 Unidade de Conservação Estadual (UCES)

```
UCES
├── id_uces (PK)
├── nome
├── categoria_manejo (protecao_integral | uso_sustentavel)
├── grupo_categoria
├── zona_insercao
├── bioma
├── municipio
├── area_total_ha
├── plano_gestao_existente (booleano)
├── plano_gestao_arquivo (opcional)
├── limites_geograficos (GeoJSON)
└── codigo_cnuc
```

### 1.5 Modalidade de Incorporação

```
MODALIDADE_INCORPORACAO
├── id_modalidade (PK)
├── codigo
├── nome (doacao_voluntaria | doacao_antecipada | compensacao_rl | compensacao_florestal | medidas_compensatorias)
├── descricao
├── base_legal
└── gera_credito (booleano)
```

---

## 2. Entidades de Certificação e Documentos

### 2.1 CACLG (Fase I)

```
CACLG
├── id_caclg (PK)
├── processo (FK → PROCESSO)
├── numero_caclg
├── data_emissao
├── data_validade
├── status (em_analise | emitida | vencida | cancelada)
├── cadeia_dominial_regular (booleano)
├── georreferenciamento_valido (booleano)
├── correspondencia_localizacao (booleano)
├── habilitado_fase_ii (booleano)
├── observacoes_iterpa
├── parecer_tecnico (FK → PARECER)
├── parecer_juridico (FK → PARECER)
├── documento_caclg (arquivo)
└── peças_tecnicas_juridicas (arquivos)
```

### 2.2 Certidão de Habilitação - CH (Fase II)

```
CERTIDAO_HABILITACAO
├── id_ch (PK)
├── processo (FK → PROCESSO)
├── caclg (FK → CACLG)
├── numero_ch
├── data_emissao
├── data_validade (2 anos)
├── data_prorrogacao (opcional, +2 anos)
├── status (em_analise | emitida | vencida | cancelada)
├── imovel_identificacao (matricula, municipio, coordenadas, area)
├── doador_beneficiario (FK → REQUERENTE)
├── uces_receptora (FK → UCES)
├── categoria_manejo
├── zona_insercao
├── area_habilitada_ha
├── modalidade_incorporacao (FK → MODALIDADE)
├── condicionantes_tecnicas_ambientais (texto)
├── condicao_necessaria_fase_iii (booleano = true)
└── documento_ch (arquivo)
```

### 2.3 Escritura Pública de Doação (Fase III)

```
ESCRITURA_DOACAO
├── id_escritura (PK)
├── processo (FK → PROCESSO)
├── ch (FK → CERTIDAO_HABILITACAO)
├── numero_escritura
├── data_lavratura
├── cartorio_notas
├── qualificacao_partes
├── descricao_imovel_geo
├── declaracao_livre_desembaracado
├── aceite_estado_pará (ITERPA)
├── clausula_destinacao_uces
├── modalidade_doacao
├── creditos_compensacao_gerados
├── condicionantes_ch (transcrição)
├── clausula_ocupacoes_tradicionais
├── despesas_responsavel (doador | estado)
├── data_registro
├── cartorio_registro_imoveis
├── status (minuta | lavrada | registrada)
└── arquivo_escritura
```

### 2.4 Certidão de Conclusão de Incorporação

```
CERTIDAO_CONCLUSAO
├── id_certidao_conclusao (PK)
├── processo (FK → PROCESSO)
├── escritura (FK → ESCRITURA_DOACAO)
├── numero_certidao
├── data_emissao
├── numero_matricula_nova_propriedade
├── area_incorporada_ha
├── uces_receptora (FK → UCES)
├── modalidade_incorporacao (FK → MODALIDADE)
├── creditos_compensacao_gerados_ha
├── data_registro
└── documento_certidao (arquivo)
```

---

## 3. Entidades de Análise e Pareceres

### 3.1 Parecer / Análise

```
PARECER
├── id_parecer (PK)
├── processo (FK → PROCESSO)
├── unidade_emitente (ITERPA | NGEO | DGMUC | DGB | PROCURADORIA_IDEFLOR | PROCURADORIA_ITERPA | PRESIDENCIA)
├── tipo_parecer (tecnico | juridico | nota_tecnica | despacho)
├── data_inicio
├── data_conclusao
├── prazo_dias_uteis
├── resultado (favoravel | favoravel_com_ressalvas | desfavoravel | diligencia)
├── conteudo
├── condicionantes
├── responsavel
└── arquivo_parecer
```

### 3.2 Análise Específica - NGEO

```
ANALISE_NGEO
├── id_analise_ngeo (PK)
├── processo (FK → PROCESSO)
├── parecer (FK → PARECER)
├── localizacao_confirmada (booleano)
├── limites_confrontados_geo (booleano)
├── cobertura_vegetal
├── estado_conservacao
├── cursos_agua_nascentes
├── edificacoes_infracoes_identificadas
├── passivos_ambientais_remoto (booleano)
├── compatibilidade_uces (booleano)
├── sobreposicao_plano_gestao (booleano)
├── vocacao_compensacao_florestal (booleano)
├── recomendacao_recebimento (booleano)
├── necessidade_visitoria_campo (booleano)
└── relatorio_tecnico (arquivo)
```

### 3.3 Análise Específica - DGMUC

```
ANALISE_DGMUC
├── id_analise_dgmuc (PK)
├── processo (FK → PROCESSO)
├── parecer (FK → PARECER)
├── imovel_inserido_integralmente (booleano)
├── imovel_inserido_parcialmente (booleano)
├── uces_alternativa_sugerida (FK → UCES, opcional)
├── compatibilidade_categoria_manejo (booleano)
├── importancia_estrategica (texto)
├── corredores_ecologicos (booleano)
├── areas_sensibilidade (booleano)
├── remanescentes_florestais (booleano)
├── conformidade_plano_gestao (booleano)
├── resultado (pertinencia | pertinencia_redirecionamento | impertinencia)
└── nota_tecnica (arquivo)
```

### 3.4 Análise Específica - DGB

```
ANALISE_DGB
├── id_analise_dgb (PK)
├── processo (FK → PROCESSO)
├── parecer (FK → PARECER)
├── potencial_conservacao (texto)
├── integridade_ecossistemas (texto)
├── pertinencia_programas_conservacao (booleano)
├── passivos_ambientais_recuperaveis (booleano)
├── medidas_recuperacao_necessarias (texto)
├── areas_app (booleano)
├── areas_rl (booleano)
├── compatibilidade_ambiental (booleano)
├── condicionantes_incorporacao (texto)
└── parecer_tecnico (arquivo)
```

### 3.5 Análise Jurídica - Procuradoria IDEFLOR-Bio

```
ANALISE_JURIDICA_IDEFLOR
├── id_analise_juridica (PK)
├── processo (FK → PROCESSO)
├── parecer (FK → PARECER)
├── regularidade_formal (booleano)
├── validade_caclg (booleano)
├── suficiencia_caclg (booleano)
├── adequacao_modalidade (booleano)
├── condicionantes_legais (texto)
├── competencia_estado (booleano)
├── tipo_despacho (deferimento | indeferimento)
├── irregularidades_sanaveis (texto)
└── minuta_despacho (arquivo)
```

---

## 4. Entidade de Créditos de Compensação

```
CREDITO_COMPENSACAO
├── id_credito (PK)
├── processo (FK → PROCESSO)
├── doador_beneficiario (FK → REQUERENTE)
├── imovel (FK → IMOVEL_RURAL)
├── certidao_conclusao (FK → CERTIDAO_CONCLUSAO)
├── modalidade (FK → MODALIDADE_INCORPORACAO)
├── credito_disponivel_ha (decimal)
├── credito_utilizado_ha (decimal)
├── saldo_disponivel_ha (decimal)
├── data_vencimento (opcional)
├── historico_utilizacao (relação → UTILIZACAO_CREDITO)
└── status (ativo | utilizado | vencido | cancelado)
```

```
UTILIZACAO_CREDITO
├── id_utilizacao (PK)
├── credito (FK → CREDITO_COMPENSACAO)
├── data_utilizacao
├── orgao_destino (SEMAS | ITERPA | outro)
├── processo_vinculado
├── hectares_utilizados
├── descricao
└── certidao_individualizada (arquivo, opcional)
```

---

## 5. Entidades de Prazos e Controle

```
PRAZO_PROCESSO
├── id_prazo (PK)
├── processo (FK → PROCESSO)
├── fase (I | II | III)
├── etapa (analise_formal | complementacao | georreferenciamento | parecer_juridico_iterpa | emissao_caclg | ngeo | dgmuc | dgb | procuradoria | presidencia | emissao_ch | minuta_escritura | registro | certidao_conclusao)
├── data_inicio
├── prazo_dias (uteis | corridos)
├── tipo_prazo (uteis | corridos)
├── data_limite
├── data_conclusao
├── prorrogado (booleano)
├── dias_prorrogacao
├── status (pendente | em_andamento | concluido | vencido)
└── responsavel
```

```
LOG_PROCESSO
├── id_log (PK)
├── processo (FK → PROCESSO)
├── data_hora
├── acao
├── unidade_responsavel
├── usuario_responsavel
├── observacoes
└── documento_vinculado (arquivo, opcional)
```

---

## 6. Diagrama de Relacionamentos

```
REQUERENTE ──1:N──► IMOVEL_RURAL ──N:1──► UCES
     │                  │
     │                  │
     ▼                  ▼
 PROCESSO ◄─────────────┘
     │
     ├──1:1──► CACLG ──1:1──► CERTIDAO_HABILITACAO ──1:1──► ESCRITURA_DOACAO ──1:1──► CERTIDAO_CONCLUSAO
     │                                                                        │
     │                                                                        ▼
     ├──1:N──► PARECER                                                  CREDITO_COMPENSACAO
     │                │                                                       │
     │                ├── ANALISE_NGEO                                        ▼
     │                ├── ANALISE_DGMUC                              UTILIZACAO_CREDITO
     │                ├── ANALISE_DGB
     │                └── ANALISE_JURIDICA_IDEFLOR
     │
     ├──1:N──► PRAZO_PROCESSO
     │
     └──1:N──► LOG_PROCESSO
```

---

## 7. Enums / Domínios

```
MODALIDADE_INCORPORACAO = [
  "doacao_voluntaria",
  "doacao_antecipada",
  "compensacao_reserva_legal",
  "compensacao_florestal",
  "medidas_compensatorias_ambientais"
]

FASE_PROCESSO = ["I", "II", "III"]

STATUS_PROCESSO = [
  "requerido",
  "em_analise_formal",
  "em_analise_georreferenciamento",
  "em_parecer_juridico_iterpa",
  "caclg_emitida",
  "em_analise_ngeo",
  "em_analise_dgmuc",
  "em_analise_dgb",
  "em_analise_juridica_ideflor",
  "em_deliberacao_presidencia",
  "ch_emitida",
  "em_elaboracao_minuta",
  "escritura_lavrada",
  "escritura_registrada",
  "concluido",
  "indeferido",
  "arquivado"
]

TIPO_PARECER = ["tecnico", "juridico", "nota_tecnica", "despacho"]

RESULTADO_PARECER = ["favoravel", "favoravel_com_ressalvas", "desfavoravel", "diligencia"]

RESULTADO_DGMUC = ["pertinencia", "pertinencia_redirecionamento", "impertinencia"]

STATUS_CACLG = ["em_analise", "emitida", "vencida", "cancelada"]

STATUS_CH = ["em_analise", "emitida", "vencida", "prorrogada", "cancelada"]

STATUS_ESCRITURA = ["minuta", "lavrada", "registrada"]

CAR_STATUS = ["ativo", "irregular", "inexistente"]

TIPO_PESSOA = ["fisica", "juridica"]

QUALIFICACAO_DOADOR = ["doador", "beneficiario", "doador_beneficiario"]
```