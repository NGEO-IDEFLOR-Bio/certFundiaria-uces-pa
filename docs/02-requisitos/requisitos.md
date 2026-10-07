# Requisitos de Sistema - IN Conjunta ITERPA / IDEFLOR-Bio

> Derivado da IN Conjunta ITERPA/IDEFLOR-Bio - Certificação Fundiária e Incorporação de Imóveis em UCES

## 1. Requisitos Funcionais

### 1.1 Fase I - Análise Fundiária pelo ITERPA (CACLG)

| ID | Requisito | Descrição | Ref. IN |
|----|-----------|-----------|---------|
| RF-01 | Requerimento CACLG | O sistema deve permitir ao requerente protocolar requerimento de emissão de CACLG, por meio físico ou eletrônico, especificando UCES de interesse e modalidade de incorporação pretendida | Art. 7º |
| RF-02 | Requerimento via SICARF | O sistema deve integrar-se ao módulo "Pedido de Certidão" da plataforma SICARF para formalização eletrônica do requerimento de CACLG | Art. 7º, §2º |
| RF-03 | Indicação de modalidade | O sistema deve exigir a indicação da UCES de interesse e da modalidade de incorporação; na ausência, subentender "doação antecipada" | Art. 7º, §3º, §4º |
| RF-04 | CACLG sem vinculação | O sistema deve permitir requerer CACLG com ou sem vinculação a processo de compensação ambiental em curso, sendo instrumento autônomo no segundo caso | Art. 7º, §5º |
| RF-05 | Documentação obrigatória | O sistema deve receber e validar a documentação exigida: (a) documentação exigida pela legislação vigente, (b) indicação de UCES, (c) indicação de modalidade, (d) extrato atualizado do CAR no SICAR | Art. 8º |
| RF-06 | Análise formal | O sistema deve suportar a análise formal da documentação pelo ITERPA | Art. 9º |
| RF-07 | Análise georreferenciamento | O sistema deve suportar a análise técnica do georreferenciamento pelo ITERPA | Art. 9º |
| RF-08 | Análise dominial | O sistema deve suportar a análise jurídica da cadeia dominial pelo ITERPA | Art. 9º |
| RF-09 | Verificações adicionais | O sistema deve suportar verificações adicionais pelo ITERPA: (a) correspondência entre localização geoespacial e UCES, (b) inexistência de óbices fundiários, (c) necessidade de ratificação/retificação | Art. 9º |
| RF-10 | Emissão CACLG | O sistema deve emitir a CACLG com menção expressa de que o imóvel está habilitado ao prosseguimento da Fase II | Art. 10 |
| RF-11 | Remessa para IDEFLOR-Bio | O sistema deve remeter o processo ao IDEFLOR-Bio após emissão da CACLG, acompanhado da certidão e peças técnicas/jurídicas | Art. 10, §2º |
| RF-12 | Complementação de documentos | O sistema deve permitir solicitar ao requerente a complementação de documentos | Art. 8º, Parágrafo único |
| RF-13 | Antecipação de análise | O ITERPA pode antecipar a análise da cobertura florestal, remetendo subsídios técnicos ao IDEFLOR-Bio | Art. 10, §1º |

### 1.2 Fase II - Análise e Habilitação pelo IDEFLOR-Bio (CH)

| ID | Requisito | Descrição | Ref. IN |
|----|-----------|-----------|---------|
| RF-14 | Autuação e distribuição | O sistema deve permitir autuação e distribuição interna sequencial: NGEO → DGMUC → Procuradoria → Presidência | Art. 11 |
| RF-15 | Análise NGEO - sobreposição | O sistema deve suportar análise de sobreposição do imóvel na UCES e monitoramento remoto por parte do NGEO | Art. 11, I |
| RF-16 | Análise NGEO - detalhada | O NGEO deve: confirmar localização e limites, verificar cobertura vegetal, identificar edificações, verificar passivos ambientais via sensoriamento remoto, avaliar compatibilidade com UCES, emitir relatório técnico | Art. 12, I-VI |
| RF-17 | Análise NGEO - sobreposição com Plano de Gestão | Indicar sobreposição com Plano de Gestão da UC e vocação para compensação florestal (sim/não) | Art. 12, VII |
| RF-18 | Relatório NGEO | O NGEO deve emitir relatório técnico fundamentado com recomendação ou não do recebimento | Art. 12, VI |
| RF-19 | Análise DGMUC | O sistema deve suportar análise de pertinência pela DGMUC: (a) inserção do imóvel na UCES, (b) compatibilidade com categoria de manejo, (c) importância estratégica, (d) corredores ecológicos, (e) conformidade com Plano de Gestão | Art. 13 |
| RF-20 | Nota Técnica DGMUC | A DGMUC deve emitir nota técnica fundamentada concluindo pela pertinência ou impertinência da incorporação | Art. 13, §1º |
| RF-21 | Análise Procuradoria | O sistema deve suportar análise jurídica pela Procuradoria: regularidade formal, validade da CACLG, adequação da modalidade, condicionantes, competência do Estado, minuta de despacho | Art. 14 |
| RF-22 | Deliberação Presidência | O sistema deve suportar deliberação final pela Presidência: deferir (com/sem condicionantes), indeferir fundamentadamente, ou determinar diligências | Art. 15 |
| RF-23 | Emissão CH | O sistema deve emitir a Certidão de Habilitação contendo todos os campos obrigatórios (Art. 16, I-IX) | Art. 16 |
| RF-24 | Validade CH | CH tem prazo de validade de 2 anos, prorrogável uma vez por igual período | Art. 16, VIII |
| RF-25 | Recurso administrativo | O sistema deve permitir recurso administrativo de indeferimento no prazo de 15 dias úteis | Art. 15, §3º, Art. 28 |

### 1.3 Fase III - Transferência do Domínio

| ID | Requisito | Descrição | Ref. IN |
|----|-----------|-----------|---------|
| RF-26 | Requerimento Fase III | O Doador deve requerer ao IDEFLOR-Bio a adoção de providências para lavratura da escritura | Art. 18 |
| RF-27 | Encaminhamento ao ITERPA | O IDEFLOR-Bio encaminha o requerimento ao ITERPA para coordenação dos procedimentos cartoriais | Art. 18, §único |
| RF-28 | Verificação de documentos | O ITERPA verifica validade dos documentos do processo e solicita atualização dos vencidos | Art. 19, I |
| RF-29 | Minuta de escritura | O ITERPA elabora minuta de escritura pública de doação com cláusulas obrigatórias (Art. 20, I-VIII) | Art. 19, II-III, Art. 20 |
| RF-30 | Agendamento cartório | O ITERPA agenda lavratura da escritura em Cartório de Notas competente | Art. 19, IV |
| RF-31 | Registro imobiliário | O ITERPA providencia registro da escritura no Cartório de Registro de Imóveis em até 30 dias corridos | Art. 21 |
| RF-32 | Comunicação ao IDEFLOR-Bio | O ITERPA comunica o registro ao IDEFLOR-Bio para fins de incorporação ao patrimônio da UCES e atualização do CNUC | Art. 21, §2º |
| RF-33 | Certidão de Conclusão | O IDEFLOR-Bio emite Certidão de Conclusão de Incorporação contendo todos os campos obrigatórios (Art. 22, I-V) | Art. 22 |

### 1.4 Gestão de Créditos de Compensação

| ID | Requisito | Descrição | Ref. IN |
|----|-----------|-----------|---------|
| RF-34 | Sistema de créditos | O IDEFLOR-Bio deve manter sistema informatizado de registro e controle dos créditos de compensação (Art. 26, I-VI) | Art. 26 |
| RF-35 | Consulta de créditos | O sistema deve permitir ao Doador Beneficiário consultar créditos disponíveis | Art. 27, §1º |
| RF-36 | Utilização de créditos | O sistema deve registrar a utilização de créditos com imediata redução do saldo disponível | Art. 27, §2º |
| RF-37 | Expedição de certidão individualizada | O IDEFLOR-Bio deve expedir certidão individualizada dos créditos disponíveis quando solicitado | Art. 27, §1º |

### 1.5 Impedimentos e Restrições

| ID | Requisito | Descrição | Ref. IN |
|----|-----------|-----------|---------|
| RF-38 | Validação de impedimentos | O sistema deve bloquear a incorporação de imóveis com: (a) pendências na cadeia dominial, (b) litígios judiciais/administrativos, (c) passivos ambientais consolidados incompatíveis, (d) sobreposição com áreas de regularização fundiária de comunidades indígenas, quilombolas ou tradicionais, (e) CAR inativo/irregular, (f) edificações incompatíveis com a UCES | Art. 6º |
| RF-39 | Superação de impedimentos | As restrições de pendência dominial e litígio podem ser superadas com sentença transitada em julgado ou decisão administrativa definitiva | Art. 6º, Parágrafo único |
| RF-40 | Ocupações tradicionais | A existência de ocupações tradicionais não impede a incorporação, desde que compatíveis com os objetivos da UCES e sujeitas a Termo de Acordo | Art. 24, §2º |
| RF-41 | Recurso administrativo | O sistema deve permitir recurso administrativo no prazo de 15 dias úteis, com efeito suspensivo | Art. 28 |
| RF-42 | Decisões compartilhadas | Decisões que envolvam competências compartilhadas devem ser apreciadas conjuntamente pelos Diretores-Presidentes do ITERPA e IDEFLOR-Bio | Art. 28, §2º |
| RF-43 | Acordo de Cooperação Técnica | Os órgãos podem celebrar ACT para compartilhamento de sistemas, bases cartográficas e outros recursos | Art. 29 |

## 2. Requisitos Não Funcionais

| ID | Requisito | Descrição | Ref. IN |
|----|-----------|-----------|---------|
| RNF-01 | Integração SICARF | O sistema deve integrar-se à plataforma SICARF (https://sicarf.pa.gov.br) para recebimento de requerimentos eletrônicos | Art. 7º, §2º |
| RNF-02 | Integração SICAR | O sistema deve integrar-se ao SICAR para validação de CAR ativo e regular | Art. 8º, III |
| RNF-03 | Integração INCRA | O sistema deve validar georreferenciamento conforme padrão técnico do INCRA | Art. 3º, XII |
| RNF-04 | Geoprocessamento | O sistema deve suportar análise de sobreposição com áreas protegidas, Terras Indígenas, Territórios Quilombolas e imóveis públicos | Art. 8º, IV |
| RNF-05 | Sensoriamento remoto | O sistema deve suportar verificação por imagens de satélite e bases cartográficas oficiais | Art. 12, II |
| RNF-06 | Publicidade | O sistema deve garantir transparência e publicidade dos processos | Art. 4º |
| RNF-07 | Segurança jurídica | O sistema deve garantir rastreabilidade e segurança jurídica em todas as etapas | Art. 4º |
| RNF-08 | Controle de prazos | O sistema deve controlar e monitorar os prazos e metas internas de SLA do processo | Operacional / SLA Interno |
| RNF-09 | Fluxo sequencial | O processo somente avança à fase seguinte após conclusão integral da fase anterior e emissão do instrumento certificatório | Art. 2º, §único |
| RNF-10 | Registro de créditos | O sistema de créditos deve manter histórico de utilização com imediata redução de saldo | Art. 26, V, Art. 27, §2º |