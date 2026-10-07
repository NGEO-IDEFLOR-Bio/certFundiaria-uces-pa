# Certificação Fundiária ITERPA / IDEFLOR-Bio

Sistema para viabilizar a **Instrução Normativa Conjunta ITERPA/IDEFLOR-Bio**, que estabelece procedimentos para certificação fundiária, habilitação e recebimento de imóveis rurais em Unidades de Conservação Estaduais do Pará.

## Estrutura do Repositório

| Documento | Descrição |
|-----------|-----------|
| [Glossário](docs/01-glossario/glossario.md) | Termos, siglas e definições extraídos do Art. 3º e disposições da IN |
| [Requisitos](docs/02-requisitos/requisitos.md) | 43 requisitos funcionais + 10 não funcionais derivados da IN 2026 |
| [Fluxos e Processos](docs/03-fluxos/fluxos.md) | Diagramas Mermaid das 3 fases, recursos, créditos e impedimentos |
| [Regras de Negócio](docs/04-regras-negocio/regras-negocio.md) | 46 regras de negócio + 7 princípios norteadores |
| [Modelo de Dados](docs/05-modelo-dados/modelo-dados.md) | Modelo conceitual com 15+ entidades e enums |
| [Backlog de Tasks](docs/06-tasks/tasks.md) | 7 épicos e 31 user stories detalhadas |
| [Quadro de Prazos](docs/07-prazos/prazos.md) | Prazos por fase com gantt e timeline Mermaid |
| [Auditoria](docs/08-auditoria/auditoria.md) | Relatório de auditoria técnica e jurídica do acervo |
| [Acervo Original](docs/00-in-original/) | IN Conjunta ITERPA/IDEFLOR-Bio 2026 (PDF/TXT) — versão assinada |
| [Histórico](docs/00-historico/) | Minuta anterior "ajustada V1" (arquivada) |
| [Processo (pae)](pae/) | Despacho e manifestações do processo administrativo |

```
├── docs/
│   ├── 00-in-original/      # IN Conjunta ITERPA/IDEFLOR-Bio 2026 (PDF e TXT) - versão assinada
│   ├── 00-historico/        # Minuta anterior "ajustada V1" (arquivada)
│   ├── 01-glossario/glossario.md
│   ├── 02-requisitos/requisitos.md
│   ├── 03-fluxos/fluxos.md
│   ├── 04-regras-negocio/regras-negocio.md
│   ├── 05-modelo-dados/modelo-dados.md
│   ├── 06-tasks/tasks.md
│   ├── 07-prazos/prazos.md
│   └── 08-auditoria/auditoria.md
├── pae/                     # Despacho e manifestações do processo administrativo
└── src/                     # Código-fonte (a definir)
```

## Resumo da IN

A IN define um processo **estritamente sequencial em 3 fases**:

| Fase | Responsável | Produto | Prazo (SLA Operacional sugerido) |
|------|------------|---------|---------------|
| **I** | ITERPA | CACLG (Certidão de Autenticidade, Correspondência de Localização e Localização Georreferenciada) | ~50 dias úteis |
| **II** | IDEFLOR-Bio | CH (Certidão de Habilitação) | ~50 dias úteis |
| **III** | ITERPA + IDEFLOR-Bio | Escritura registrada + Certidão de Conclusão de Incorporação | ~55 dias corridos |

### Modalidades de Incorporação
1. Doação voluntária
2. Doação antecipada
3. Compensação de Reserva Legal
4. Compensação florestal
5. Cumprimento de medidas compensatórias ambientais

### Atuação por Fase

**Fase I (ITERPA):** Análise formal → Análise georreferenciamento → Parecer jurídico → Emissão CACLG

**Fase II (IDEFLOR-Bio):** NGEO (sensoriamento remoto) → DGMUC (pertinência) → Procuradoria (jurídico) → Presidência (deliberação) → Emissão CH

**Fase III (ITERPA + IDEFLOR-Bio):** Minuta de escritura → Lavratura → Registro → Certidão de Conclusão