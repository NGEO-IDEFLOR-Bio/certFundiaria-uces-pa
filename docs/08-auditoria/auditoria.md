# AUDITORIA — Certificação Fundiária e Incorporação de Imóveis em UCES (ITERPA/IDEFLOR-Bio)

> **Documento de Auditoria Especializada** — Direito Ambiental, Direito Fundiário, Geoprocessamento e Gestão Pública
> **Objeto:** Instrução Normativa Conjunta ITERPA/IDEFLOR-Bio (recepção de imóveis rurais em UCES) e documentação técnica derivada
> **Data da análise:** 07/10/2026
> **Corpus auditado:** `docs/00-in-original/` (IN assinada 2026), `docs/00-historico/` (minuta V1), `docs/01-..07`, README e acervo `pae/`
> **Fonte normativa canônica:** **IN Conjunta ITERPA/IDEFLOR-Bio de 30/06/2026** (assinada eletronicamente em 02/07/2026) — `docs/00-in-original/IN_Conjunta_ITERPA_IDEFLOR-Bio_2026.txt`

---

## VEREDITO EXECUTIVO

O projeto **chegou à IN assinada** em boa forma: competências corretas, fluxo sequencial bem desenhado, rito recursal compatível com a LEPA/PA e modelagem técnica de qualidade. Entretanto, o repositório operava com **duas versões conflitantes da IN** (a pasta "original" guardava uma minuta obsoleta e mal numerada), o que afetava a rastreabilidade de todos os documentos derivados.

**Situação pós-intervenção:** a duplicidade foi resolvida (V1 arquivada em `00-historico/`; IN 2026 promovida a `00-in-original/`), e as divergências de consistência foram corrigidas. O que resta para **aprovação plena da IN para publicação** são **4 riscos jurídicos de mérito** (especialmente a criação de "crédito em hectares" por IN), **2 erros formais na versão assinada** e lacunas de implementação do sistema.

---

## METODOLOGIA

- Extração e leitura integral da IN **assinada (2026)** e da **minuta V1** (comparação).
- Leitura dos 7 documentos derivados (`glossario`, `requisitos`, `fluxos`, `regras-negocio`, `modelo-dados`, `tasks`, `prazos`), das imagens Mermaid e do acervo `pae/` (Despacho e Manifestação NGEO).
- Verificação das citações legais contra o Código Florestal (Lei 12.651/2012), SNUC (Lei 9.985/2000), CONAMA 371/2006, LEPA (Lei 8.972/2020) e as competências do ITERPA (Lei 4.584/1975, Decreto 1.190/2020) e do IDEFLOR-Bio (Lei 6.963/2007).

---

## 1. ACHADO PRINCIPAL — Duplicidade de versões canônicas (RESOLVIDO)

Antes desta intervenção o repositório continha:

| Item | `docs/00-in-original/` (**antigo**) | IN **2026 assinada** (`pae/`) |
| :--- | :--- | :--- |
| Natureza | Minuta "ajustada V1" (obsoleta) | IN assinada (30/06/2026) |
| Numeração de artigos | **Corrompida** (dois "Art. 20/21", Art. 14 após Art. 21, "III" duplicado, dois "Capítulo IX", Arts. 38-40 interpostos) | **Correta** (Arts. 1º–33, 10 capítulos) |
| DGB no fluxo da Fase II | Presente | Removida |
| Redirecionamento a outra UCES | Presente | Removido |
| Vedação de área < módulo fiscal | Presente | Removida |
| Prazos internos como norma | Arts. 38-40 | Removidos (metas de SLA) |
| Uso de créditos perante ITERPA | Art. 27, II | Removido (SEMAS + "outros órgãos competentes") |
| Citação da compensação de RL | art. 44, III (**incorreta**) | art. 66, §5º, III (**correta**) |
| URL SICARF | `sicarf.semas.pa.gov.br` | `sicarf.pa.gov.br` |

**Ações executadas:**
1. Criada a pasta `docs/00-historico/` e movidas as 3 versões da **minuta V1** (docx/pdf/txt).
2. Promovida a **IN Conjunta 2026 assinada** (pdf/txt) de `pae/` para `docs/00-in-original/` como **documento original canônico**.
3. README atualizado com a nova estrutura.

---

## 2. EIXO 1 — CONFORMIDADE LEGAL ESTRITA (IN 2026 assinada)

### 2.1. Pontos sólidos (sem risco)
- Competências: ITERPA (terras públicas estaduais — Lei 4.584/1975, Decreto 1.190/2020) e IDEFLOR-Bio (UC estaduais — Lei 6.963/2007 e alterações) — bem fundamentadas nos considerandos.
- Compensação de Reserva Legal ancorada no **art. 66, § 5º, III, da Lei 12.651/2012** (a V1 citava art. 44 — incorreto; corrigido na versão assinada).
- Vedações do Art. 6º (pendências dominiais, litígios, passivos, sobreposição com áreas de TI/quilombolas/tradicionais, CAR irregular, edificações incompatíveis) — coerentes e auditáveis por GIS.
- Recurso em **15 dias úteis**, efeito suspensivo e decisão motivada (Arts. 15, §3º e 28) — **compatível com a LEPA (Lei 8.972/2020)**.

### 2.2. 🔴 Riscos de ilegalidade a resolver antes da publicação

**L1. "Crédito em hectares" criado por IN, sem base legislativa.** A IN institui crédito fungível de compensação (Art. 3º, IX; Art. 5º, §2º; Arts. 26-27) utilizável perante a SEMAS. O ordenamento não prevê esse crédito genérico — existem instrumentos próprios: **CRA (Cota de Reserva Ambiental)**, **compensação de RL (art. 66, §5º)**, **compensação ambiental (art. 36 da Lei 9.985/2000 + CONAMA 371/2006)** e **reposição florestal (arts. 33-35 do Código Florestal)**. **Criar crédito transacionável por IN invade reserva legal.** Recomenda-se: (a) restringir a IN ao reconhecimento dos instrumentos legais existentes, **ou** (b) encaminhar **projeto de lei estadual** que crie o instrumento.

**L2. Redação "propriedade com supressão de Reserva Legal" (Art. 5º, III).** Sugere admitir imóvel que suprimiu RL (vedado como passivo no Art. 6º, III). Corrigir para "imóvel **com déficit de Reserva Legal** passível de compensação na forma do art. 66, § 5º, III, da Lei 12.651/2012".

**L3. Proporção fixa 1:1 (Art. 5º, §1º).** a lei federal exige equivalência em **área e importância ecológica** no mesmo bioma. Recomenda-se: "equivalência em área e importância ecológica, observada a legislação federal; a proporção 1:1 aplica-se subsidiariamente".

**L4. Medidas compensatórias ambientais (Art. 3º, VIII; Art. 5º, V).** A compensação ambiental de impacto significativo segue a sistemática do **art. 36 da Lei 9.985/2000** e da **CONAMA 371/2006** (CCA), não equivalência ha-a-ha de área suprimida. Referir expressamente e coordenar com SEMAS/CCA.

### 2.3. Alertas de competência
- **L5.** A CACLG atesta "georreferenciamento válido" (Art. 3º, X) — registrar que a CACLG é **certificação dominial estadual**, sem substituir a certificação do INCRA no SIGEF (Lei 10.267/2001).
- **L6.** Citar a **LEPA (Lei 8.972/2020)** nos considerandos como fundamento do rito recursal.

### 2.4. 🟠 Formais na versão assinada (corrigir antes do DOE)
- **F1. Art. 6º, IV — frase quebrada:** "imóveis **cujo com** áreas de regularização fundiária..." → "imóveis **cujo georreferenciamento apresente sobreposição com** áreas de regularização fundiária de comunidades indígenas, quilombolas ou tradicionais".
- **F2. Assinatura:** a minuta indica os Presidentes (Kono Ramos / Nilson Pinto), mas a assinatura eletrônica registrada é de **Fernanda Jorge Sequeira (02/07/2026)** — verificar procuração/representação; IN Conjunta deve emanar dos titulares.
- **F3. Nº da IN** em branco ("____/2026") — completar na publicação.

---

## 3. EIXO 2 — RITOS E SEGURANÇA JURÍDICA

- **Sequencialidade estrita (Art. 2º, §único):** correto; evita retrabalho com imóveis de cadeia viciada.
- **Recurso (Arts. 15, §3º; 28):** 15 dias úteis, efeito suspensivo, decisão motivada, apreciação conjunta em competência compartilhada — bom.
- **Lacunas:** falta prazo para a Administração decidir o recurso (silêncio administrativo — usar a LEPA como supletiva); falta fonte de custeio da realocação/adequação de ocupações incompatíveis (Arts. 24-25).
- **Risco de dupla emissão de crédito:** a CH formaliza o crédito (Art. 5º, §2º) e a CCI também registra créditos (Art. 22, V). Definir regra única: **crédito nasce na CH e se consuma/registra definitivamente na CCI**, com vedação de dupla contabilização.

---

## 4. EIXO 3 — RIGOR TÉCNICO DO SISTEMA (docs 01-07)

**Qualidade:** modelo conceitual (15+ entidades), 7 épicos, diagramas Mermaid e a distinção **prazo legal × meta de SLA** (`prazos.md`) estão sólidos e aderentes à IN 2026.

### 4.1. Divergências já CORRIGIDAS nesta intervenção (07/10/2026)

| Doc | Correção aplicada |
| :-- | :--- |
| `01-glossario` | URL SICARF → `https://sicarf.pa.gov.br`; "vertices"→"vértices"; "actualizado"→"atualizado" |
| `02-requisitos` | RF-05 sem o item "relatório de sobreposição" (não é documento na IN 2026); referência a "legislação vigente" em vez de "IN 001/2022"; RNF-01 URL |
| `03-fluxos` | Lista de documentação mínima da Fase I sem o relatório de sobreposição (com nota de que a verificação ocorre na análise — Arts. 9º, I e 12) |
| `04-regras-negocio` | RN-18 idem RF-05 |
| `06-tasks` | URL SICARF |
| `02/04/06` | **Renumeração sequencial**: RF-01..43, RNF-01..10, RN-01..46, STORY-01.1..07.3 (removidas lacunas) |

### 4.2. Itens remanescentes (não bloqueiam, mas recomenda-se)
- `05-modelo-dados`: CACLG com `data_validade` — a IN 2026 **não fixa validade da CACLG** (só da CH) → marcar como definível em ato próprio ou remover.
- `05-modelo-dados`: add entidades **OCUPAÇÃO_TRADICIONAL, BENFEITORIA, TERMO_ACORDO, CONDICIONANTE** (objetos centrais dos Arts. 24-25 e da CH).
- `02-requisitos`/`modelo`: garantir RF explícito para **vistoria de campo** (Art. 11, I) — o modelo já possui `necessidade_visitoria_campo`.
- Alinhar os **totais** do README aos valores reais (43 RF / 10 RNF / 46 RN).

---

## 5. EIXO 4 — DADOS, TRANSPARÊNCIA E INTEGRAÇÃO

- **Publicidade (Art. 4º) e rastreabilidade:** atendidos pelo desenho.
- **LGPD:** recomenda-se prever o tratamento de dados pessoais do Doador/requerente (protocolo, certidões) e a SEMAS/IDEFLOR como controladores/operadores.
- **Integração com o ecossistema estadual:** além do **CNUC** (Art. 22), recomenda-se atualizar o **SEINUC/PA** (Lei 10.306/2023) e comunicar a **SEMAS** para efeitos do **ICMS Verde** — ponte natural com o projeto SEINUC/PA.

---

## 6. MATRIZ DE RISCOS (ordenação)

| # | Risco | Severidade | Status |
| :-- | :--- | :---: | :---: |
| 1 | Duplicidade de versões da IN (V1 × 2026) | 🔴 Crítico | ✅ Resolvido |
| 2 | Crédito "em hectares" sem base legislativa (L1) | 🔴 Crítico | ⏳ Aberto |
| 3 | Redação "supressão de RL" (L2) | 🟠 Alto | ⏳ Aberto |
| 4 | Proporção 1:1 automática (L3) | 🟠 Alto | ⏳ Aberto |
| 5 | Medidas compensatórias sem coordenação SNUC/CONAMA (L4) | 🟠 Alto | ⏳ Aberto |
| 6 | Erro formal Art. 6º, IV (F1) | 🟠 Alto | ⏳ Aberto |
| 7 | Divergência de assinatura (F2) | 🟠 Alto | ⏳ Verificar |
| 8 | Dupla geração de crédito CH × CCI | 🟡 Médio | ⏳ Aberto |
| 9 | Não citação da LEPA (L6) | 🟡 Médio | ⏳ Aberto |
| 10 | "Certificação" ITERPA × INCRA (L5) | 🟡 Médio | ⏳ Aberto |
| 11 | Limites `data_validade` CACLG / entidades do modelo | 🟡 Médio | ⏳ Recomenda-se |
| 12 | Integração SEINUC/ICMS Verde | 🟡 Médio | ⏳ Recomenda-se |

---

## 7. PLANO DE AÇÃO RECOMENDADO

1. **Jurídico (PGE/PA):** dirimir L1 (projeto de lei ou restrição aos instrumentos legais), L2, L3, L4 e corrigir F1/F2 antes do envio ao DOE.
2. **Consistência:** registrar `data_validade` da CACLG, incluir entidades do modelo, formalizar RF de vistoria e integrar SEINUC/ICMS Verde.
3. **Implementação do sistema:** seguir os 7 épicos; antes do primeiro ciclo real, definir SLA, integrações (SICARF, SICAR, INCRA, bases) e controle de créditos com prevenção de dupla contabilização.
4. **Próxima revisão da IN:** editar a IN 2026 (não a V1) e republicar em `docs/00-in-original/`, mantendo V1 apenas em `00-historico/`.

---

## 8. RECOMENDAÇÃO FINAL

A IN 2026 está **aprovável com ressalvas**: os riscos de mérito (L1–L4) e os erros formais (F1–F2) devem ser sanados pela PGE/PA antes da publicação no DOE, e o sistema deve ser implementado com os controles apontados. A governança documental do repositório está agora saneada.

> **Observação de método:** as citações legais foram conferidas contra a legislação federal e estadual citada; a IN oficial (2026) é a única fonte normativa canônica do projeto — a minuta "V1" deve ser tratada estritamente como histórico.

*Relatório de auditoria — encerramento da primeira rodada (07/10/2026).*