# Backlog de Tasks - Sistema de Certificação Fundiária e Incorporação de Imóveis em UCES

> Derivado da IN Conjunta ITERPA/IDEFLOR-Bio

## Épicos

### EPIC-01: Gestão de Processos e Protocolo
Sistema de protocolo e tramitação de processos entre ITERPA e IDEFLOR-Bio, com controle de fases sequenciais.

### EPIC-02: Fase I - Análise Fundiária (ITERPA)
Funcionalidades para análise fundiária, georreferenciamento e emissão de CACLG pelo ITERPA.

### EPIC-03: Fase II - Análise e Habilitação (IDEFLOR-Bio)
Funcionalidades para análise de pertinência, compatibilidade ambiental, análise jurídica e emissão de CH pelo IDEFLOR-Bio.

### EPIC-04: Fase III - Transferência de Domínio
Funcionalidades para elaboração de minuta, lavratura e registro de escritura, e emissão de Certidão de Conclusão.

### EPIC-05: Sistema de Créditos de Compensação
Registro, controle e utilização de créditos de compensação em hectares.

### EPIC-06: Integrações Externas
Integrações com SICARF, SICAR, INCRA e bases cartográficas.

### EPIC-07: Controle de Prazos e Acompanhamento
Monitoramento de prazos, notificações e dashboard de acompanhamento.

---

## EPIC-01: Gestão de Processos e Protocolo

### STORY-01.1: Requerimento do Interessado
- **Como** requerente
- **Quero** protocolar um requerimento de CACLG (físico ou eletrônico)
- **Para** iniciar o processo de certificação fundiária
- **Critérios de aceite**:
  - O requerimento deve permitir indicação de UCES de interesse
  - O requerimento deve permitir indicação de modalidade de incorporação
  - Na ausência de modalidade, o sistema assume "doação antecipada"
  - Deve ser possível requerer com ou sem vinculação a processo de compensação
  - O sistema deve gerar número de processo único e rastreável
- **Ref. IN**: Art. 7º

### STORY-01.2: Upload e Validação de Documentação
- **Como** requerente
- **Quero** enviar a documentação obrigatória digitalmente
- **Para** instruction o processo
- **Critérios de aceite**:
  - Documentação exigida pela IN ITERPA 001/2022 (checklist configurável)
  - Indicação da UCES de interesse
  - Indicação da modalidade de incorporação
  - Extrato atualizado do CAR no SICAR
  - Relatório de sobreposição com áreas protegidas
  - O ITERPA pode exigir documentação complementar
- **Ref. IN**: Art. 8º

### STORY-01.3: Tramitação Sequencial de Fases
- **Como** analista
- **Quero** que o processo siga estritamente as 3 fases sequenciais
- **Para** garantir conformidade com a IN
- **Critérios de aceite**:
  - O processo não pode avançar à Fase II sem CACLG emitida
  - O processo não pode avançar à Fase III sem CH emitida
  - Cada fase deve ter seu instrumento certificatório emitido
  - O status do processo deve refletir a fase atual
- **Ref. IN**: Art. 2º

### STORY-01.4: Log de Tramitação
- **Como** qualquer ator do processo
- **Quero** visualizar o histórico completo de tramitação
- **Para** rastrear todas as ações e decisões
- **Critérios de aceite**:
  - Registrar data/hora, ação, unidade e responsável
  - Registrar documentos vinculados
  - Registrar prazos e cumprimentos
- **Ref. IN**: Art. 4º (publicidade, segurança jurídica)

### STORY-01.5: Recurso Administrativo
- **Como** requerente
- **Quero** interpor recurso administrativo contra indeferimento
- **Para** buscar revisão da decisão
- **Critérios de aceite**:
  - Prazo de 15 dias úteis para recurso
  - Efeito suspensivo automático (salvo decisão em contrário)
  - Decisões compartilhadas devem ser apreciadas conjuntamente
  - Notificação ao ITERPA quando envolver aspectos fundiários
- **Ref. IN**: Art. 28

---

## EPIC-02: Fase I - Análise Fundiária (ITERPA)

### STORY-02.1: Análise Formal da Documentação
- **Como** analista do ITERPA
- **Quero** realizar a análise formal da documentação
- **Para** verificar completude e conformidade
- **Critérios de aceite**:
  - Prazo de 10 dias úteis
  - Possibilidade de solicitar complementação de documentos (30 dias corridos)
  - Checklists de documentos obrigatórios
  - Registro de pendências e solicitações
- **Ref. IN**: Art. 38, I-II

### STORY-02.2: Análise Técnica do Georreferenciamento
- **Como** analista do ITERPA
- **Quero** realizar a análise técnica do georreferenciamento
- **Para** verificar correspondência com UCES e inexistência de óbices fundiários
- **Critérios de aceite**:
  - Prazo de 20 dias úteis
  - Verificação de correspondência geoespacial com UCES
  - Verificação de inexistência de óbices fundiários
  - Verificação de necessidade de ratificação/retificação
  - Integração com padrão INCRA
- **Ref. IN**: Art. 9º, Art. 38, III

### STORY-02.3: Parecer Jurídico ITERPA
- **Como** procurador do ITERPA
- **Quero** emitir parecer jurídico sobre a cadeia dominial
- **Para** atestar regularidade fundiária
- **Critérios de aceite**:
  - Prazo de 15 dias úteis
  - Análise da cadeia dominial
  - Verificação de consistência registral e dominial
  - Identificação de necessidade de regularização
- **Ref. IN**: Art. 38, IV

### STORY-02.4: Emissão da CACLG
- **Como** Diretor-Presidente do ITERPA
- **Quero** emitir a CACLG
- **Para** habilitar o imóvel para prosseguimento ao IDEFLOR-Bio
- **Critérios de aceite**:
  - Prazo de 5 dias úteis após aprovação
  - Menção expressa de habilitação para Fase II
  - Remessa automática do processo ao IDEFLOR-Bio
  - Notificação ao requerente
- **Ref. IN**: Art. 10, Art. 38, V

### STORY-02.5: Verificação de Impedimentos Fundiários
- **Como** analista do ITERPA
- **Quero** verificar os impedimentos previstos no Art. 6º
- **Para** bloquear imóveis com pendências
- **Critérios de aceite**:
  - Verificar pendências na cadeia dominial (sobreposição com áreas públicas)
  - Verificar litígios judiciais/administrativos
  - Verificar passivos ambientais incompatíveis
  - Verificar sobreposição com propriedades certificadas INCRA
  - Verificar CAR ativo e regular
  - Verificar área inferior ao módulo fiscal (com exceção de complementação)
  - Verificar edificações incompatíveis com UCES
  - Permitir superação com sentença transitada em julgado
- **Ref. IN**: Art. 6º

### STORY-02.6: Antecipação de Análise Florestal
- **Como** analista do ITERPA
- **Quero** antecipar a análise de cobertura florestal e remeter subsídios ao IDEFLOR-Bio
- **Para** agilizar a Fase II
- **Critérios de aceite**:
  - Registrar a antecipação no processo
  - Disponibilizar subsídios técnicos ao IDEFLOR-Bio
- **Ref. IN**: Art. 10, §1º

---

## EPIC-03: Fase II - Análise e Habilitação (IDEFLOR-Bio)

### STORY-03.1: Distribuição Interna do Processo
- **Como** Presidência do IDEFLOR-Bio
- **Quero** distribuir o processo internamente de forma sequencial
- **Para** garantir o fluxo NGEO → DGMUC → DGB → Procuradoria → Presidência
- **Critérios de aceite**:
  - Autuação automática ao receber processo do ITERPA
  - Distribuição sequencial obrigatória
  - O processo só avança à etapa seguinte após conclusão da anterior
  - Registro de recebimento por cada unidade
- **Ref. IN**: Art. 11

### STORY-03.2: Análise do NGEO
- **Como** analista do NGEO
- **Quero** realizar a checagem e monitoramento remoto
- **Para** verificar sobreposição e condições do imóvel
- **Critérios de aceite**:
  - Confirmar localização e limites confrontando com georreferenciamento ITERPA
  - Verificar cobertura vegetal, cursos d'água, nascentes
  - Identificar edificações e intervenções humanas
  - Verificar passivos ambientais por sensoriamento remoto
  - Avaliar compatibilidade com UCES receptora
  - Indicar sobreposição com Plano de Gestão
  - Indicar vocação para compensação florestal (sim/não)
  - Emitir relatório técnico com recomendação ou não
  - Prazo: 20 dias úteis (+10 prorrogáveis)
- **Ref. IN**: Art. 12

### STORY-03.3: Análise de Pertinência (DGMUC)
- **Como** analista da DGMUC
- **Quero** realizar a análise de pertinência da incorporação
- **Para** avaliar se o imóvel é adequado à UCES
- **Critérios de aceite**:
  - Verificar inserção integral ou parcial na UCES
  - Avaliar compatibilidade com categoria de manejo
  - Avaliar importância estratégica para consolidação/ampliação da UCES
  - Identificar corredores ecológicos e áreas de sensibilidade
  - Verificar conformidade com Plano de Gestão
  - Emitir nota técnica: pertinência / pertinência com redirecionamento / impertinência
  - Prazo: 10 dias úteis
  - Em caso de redirecionamento, consultar requerente (10 dias úteis)
- **Ref. IN**: Art. 13

### STORY-03.4: Análise de Compatibilidade Ambiental (DGB)
- **Como** analista da DGB
- **Quero** realizar a análise de compatibilidade ambiental
- **Para** avaliar se o imóvel é adequado para conservação
- **Critérios de aceite**:
  - Avaliar potencial de conservação e integridade de vegetação nativa
  - Avaliar relevância para conectividade de habitats e serviços ecossistêmicos
  - Avaliar pertinência para programas de conservação e pesquisa
  - Verificar compatibilidade de passivos ambientais
  - Verificar APP e RL conforme CAR
  - Emitir parecer técnico
  - Condições recuperáveis geram condicionantes para CH e escritura
  - Prazo: 15 dias úteis
- **Ref. IN**: Art. 21

### STORY-03.5: Análise Jurídica (Procuradoria)
- **Como** procurador do IDEFLOR-Bio
- **Quero** realizar a análise jurídica
- **Para** verificar regularidade e legalidade
- **Critérios de aceite**:
  - Verificar regularidade formal e cumprimento de etapas/prazos
  - Verificar validade e suficiência da CACLG
  - Verificar adequação da modalidade à legislação
  - Analisar condicionantes/ressalvas
  - Verificar competência do Estado para receber imóvel
  - Elaborar minuta de despacho de deferimento/indeferimento
  - Identificar irregularidades sanáveis
  - Prazo: 10 dias úteis
- **Ref. IN**: Art. 14

### STORY-03.6: Deliberação e Emissão da CH
- **Como** Diretor-Presidente do IDEFLOR-Bio
- **Quero** deliberar e emitir a Certidão de Habilitação
- **Para** habilitar ou não o imóvel para Fase III
- **Critérios de aceite**:
  - Deliberação com base no conjunto de manifestações
  - Pode deferir com/sem condicionantes, indeferir, ou determinar diligências
  - Prazo de deliberação: 5 dias úteis
  - Prazo de emissão da CH: 5 dias úteis após deliberação
  - CH deve conter todos os campos obrigatórios (Art. 16, I-IX)
  - Validade da CH: 2 anos, prorrogáveis por mais 2 anos
  - Indeferimento deve ser motivado e comunicado ao requerente e ITERPA
- **Ref. IN**: Art. 15, Art. 16

---

## EPIC-04: Fase III - Transferência de Domínio

### STORY-04.1: Requerimento para Lavratura de Escritura
- **Como** Doador
- **Quero** requerer ao IDEFLOR-Bio as providências para lavratura da escritura
- **Para** iniciar a Fase III
- **Critérios de aceite**:
  - CH vigente é condição necessária
  - IDEFLOR-Bio encaminha ao ITERPA
- **Ref. IN**: Art. 18

### STORY-04.2: Elaboração de Minuta de Escritura
- **Como** analista do ITERPA
- **Quero** elaborar a minuta de escritura pública de doação
- **Para** formalizar a transferência do domínio
- **Critérios de aceite**:
  - Verificação de validade dos documentos (solicitar atualização dos vencidos)
  - Minuta com cláusulas obrigatórias (Art. 20, I-VIII)
  - Inclusão de condicionantes da CH
  - Prazo: 15 dias úteis
- **Ref. IN**: Art. 19, Art. 20

### STORY-04.3: Registro da Escritura
- **Como** analista do ITERPA
- **Quero** providenciar o registro da escritura no Cartório de Imóveis
- **Para** incorporar o imóvel ao patrimônio do Estado
- **Critérios de aceite**:
  - Registro em até 30 dias corridos após lavratura
  - Despesas cartorárias de responsabilidade do Doador (regra geral)
  - Comunicação ao IDEFLOR-Bio após registro
- **Ref. IN**: Art. 21

### STORY-04.4: Emissão de Certidão de Conclusão
- **Como** analista do IDEFLOR-Bio
- **Quero** emitir a Certidão de Conclusão de Incorporação
- **Para** finalizar o processo
- **Critérios de aceite**:
  - Conter: número de matrícula, área incorporada, UCES receptora, modalidade, créditos gerados
  - Prazo: 10 dias úteis após registro
  - Atualização do CNUC
- **Ref. IN**: Art. 22

---

## EPIC-05: Sistema de Créditos de Compensação

### STORY-05.1: Registro de Créditos
- **Como** IDEFLOR-Bio
- **Quero** registrar os créditos de compensação gerados
- **Para** controlar o saldo disponível de cada Doador Beneficiário
- **Critérios de aceite**:
  - Identificação do Doador Beneficiário
  - Imóvel incorporado com matrícula e área em hectares
  - Modalidade de compensação
  - Crédito disponível em hectares
  - Histórico de utilização
  - Data de vencimento (se aplicável)
- **Ref. IN**: Art. 26

### STORY-05.2: Consulta de Créditos
- **Como** Doador Beneficiário
- **Quero** consultar meus créditos de compensação disponíveis
- **Para** utilizar em processos de regularização
- **Critérios de aceite**:
  - Visualizar saldo disponível em hectares
  - Visualizar histórico de utilização
  - Visualizar data de vencimento
- **Ref. IN**: Art. 27, §1º

### STORY-05.3: Utilização de Créditos
- **Como** Doador Beneficiário
- **Quero** utilizar créditos perante SEMAS, ITERPA ou outros órgãos
- **Para** regularizar obrigações ambientais ou fundiárias
- **Critérios de aceite**:
  - Registrar utilização com imediata redução do saldo
  - Permitir utilização perante SEMAS, ITERPA e outros órgãos
  - Expedir certidão individualizada quando solicitado
- **Ref. IN**: Art. 27

---

## EPIC-06: Integrações Externas

### STORY-06.1: Integração com SICARF
- **Como** sistema
- **Quero** integrar-me com o módulo "Pedido de Certidão" da plataforma SICARF
- **Para** receber requerimentos eletrônicos de CACLG
- **Critérios de aceite**:
  - Recebimento de requerimentos eletrônicos
  - Indicação expressa de que o pedido se destina a fins desta IN
  - URL: https://sicarf.semas.pa.gov.br
- **Ref. IN**: Art. 7º, §2º

### STORY-06.2: Integração com SICAR
- **Como** sistema
- **Quero** integrar-me com o SICAR para validar CAR ativo e regular
- **Para** verificar o requisito do Art. 6º, V
- **Critérios de aceite**:
  - Validação de CAR ativo e regular
  - Obtenção de extrato atualizado do CAR
- **Ref. IN**: Art. 6º, V, Art. 8º, III

### STORY-06.3: Integração com INCRA (Georreferenciamento)
- **Como** sistema
- **Quero** validar o georreferenciamento conforme padrão técnico do INCRA
- **Para** garantir conformidade com a IN
- **Critérios de aceite**:
  - Validação de sobreposição com propriedades certificadas pelo INCRA
  - Validação de georreferenciamento ao Sistema Geodésico Brasileiro
- **Ref. IN**: Art. 3º, XIII, Art. 6º, IV

### STORY-06.4: Integração com Bases Cartográficas
- **Como** sistema
- **Quero** integrar-me com bases cartográficas oficiais para análise de sobreposição
- **Para** gerar relatórios de sobreposição com áreas protegidas, TI, TQ e imóveis públicos
- **Critérios de aceite**:
  - Sobreposição com UCES
  - Sobreposição com Terras Indígenas
  - Sobreposição com Territórios Quilombolas
  - Sobreposição com imóveis públicos federais/estaduais/municipais
  - Sobreposição com Plano de Gestão da UCES
- **Ref. IN**: Art. 8º, IV, Art. 12

### STORY-06.5: Integração com CNUC
- **Como** sistema
- **Quero** atualizar o CNUC após registro do imóvel
- **Para** manter o cadastro atualizado
- **Critérios de aceite**:
  - Atualização automática após registro da escritura
- **Ref. IN**: Art. 21, §2º

---

## EPIC-07: Controle de Prazos e Acompanhamento

### STORY-07.1: Dashboard de Acompanhamento
- **Como** gestor
- **Quero** visualizar um dashboard com todos os processos e suas fases
- **Para** acompanhar o andamento e identificar gargalos
- **Critérios de aceite**:
  - Processos por fase (I, II, III)
  - Processos por etapa dentro de cada fase
  - Processos com prazos vencidos ou próximos do vencimento
  - Tempo médio por etapa
  - Filtros por órgão, unidade, status, UCES, modalidade

### STORY-07.2: Controle de Prazos
- **Como** responsável por etapa
- **Quero** ser notificado sobre prazos
- **Para** cumprir os prazos definidos na IN
- **Critérios de aceite**:
  - Cálculo automático de prazos (úteis/corridos conforme a etapa)
  - Alertas de vencimento próximo
  - Registro de prorrogações quando aplicável
  - Quadro resumo de prazos conforme Art. 38-40

### STORY-07.3: Reunião Mensal de Alinhamento
- **Como** servidor designado
- **Quero** registrar as reuniões mensais de alinhamento operacional
- **Para** documentar o controle institucional
- **Critérios de aceite**:
  - Agendamento e registro de reuniões mensais
  - Pauta e ata
  - Deliberações e ações
- **Ref. IN**: Art. 42

### STORY-07.4: Relatórios Gerenciais
- **Como** Diretor-Presidente
- **Quero** gerar relatórios gerenciais
- **Para** acompanhar estatísticas e tomar decisões
- **Critérios de aceite**:
  - Processos por modalidade
  - Processos por UCES
  - Processos por fase e etapa
  - Tempo médio por fase
  - Taxa de deferimento/indeferimento
  - Créditos de compensação gerados e utilizados