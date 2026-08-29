# Regras de Negócio — VanTrack

As regras de negócio definem restrições, condições e comportamentos
do domínio do VanTrack que devem ser respeitados pelo sistema.

---

## RN-001 — Acesso vinculado à empresa

**Título:**  
Acesso ao sistema por código de vinculação.

**Descrição:**  
O acesso ao acompanhamento de uma van deve ocorrer por meio de um código
fornecido pela empresa de transporte.

**Origem:**  
Definição do modelo de acesso do VanTrack.

**Stakeholders envolvidos:**  
Responsável, aluno, motorista e empresa de transporte.

**Condição:**  
Aplicada durante o primeiro acesso ou vinculação do usuário.

**Regra:**  
O usuário somente poderá acessar informações de uma van após utilizar
um código válido fornecido pela empresa responsável pelo transporte.

**Exceções:**  
Nenhuma identificada.

**Dados envolvidos:**  
Usuário, empresa, van, código de vinculação.

**Prioridade:**  
Alta

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-001, RF-013, RNF-002

**Observações:**  
Nenhuma.

---

## RN-002 — Restrição de acesso aos dados do aluno

**Título:**  
Acesso restrito às informações do aluno vinculado.

**Descrição:**  
Responsáveis devem acessar somente as informações dos alunos sob sua responsabilidade.

**Origem:**  
Necessidade de privacidade e controle de acesso aos dados dos usuários.

**Stakeholders envolvidos:**  
Responsável, aluno e empresa de transporte.

**Condição:**  
Aplicada sempre que um responsável consultar informações no sistema.

**Regra:**  
O responsável somente poderá visualizar a localização da van vinculada
ao seu aluno e as informações dos alunos sob sua responsabilidade.

**Exceções:**  
Um responsável poderá possuir mais de um aluno vinculado à sua conta.

**Dados envolvidos:**  
Responsável, aluno, vínculo responsável-aluno, van e rota.

**Prioridade:**  
Crítica

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-001, RF-002, RF-003, RF-011, RF-012, RF-013, RNF-002

**Observações:**  
Nenhuma.

---

## RN-003 — Consentimento para tratamento de localização

**Título:**  
Consentimento obrigatório para utilização de dados de localização.

**Descrição:**  
Os dados de localização somente poderão ser coletados, utilizados ou
compartilhados mediante consentimento do titular dos dados ou de seu
responsável legal, quando aplicável.

**Origem:**  
Necessidade de proteção de dados pessoais e de localização.

**Stakeholders envolvidos:**  
Responsável, aluno, motorista e empresa de transporte.

**Condição:**  
Aplicada antes do início do compartilhamento de localização.

**Regra:**  
O sistema não deverá iniciar o compartilhamento de localização sem que
exista consentimento válido registrado.

**Exceções:**  
Nenhuma definida no escopo atual do VanTrack.

**Dados envolvidos:**  
Usuário, consentimento, data e horário do consentimento.

**Prioridade:**  
Crítica

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-002, RF-003, RNF-002

**Observações:**  
Nenhuma.

---

## RN-004 — Prazo para confirmação de presença

**Título:**  
Confirmação de utilização do transporte.

**Descrição:**  
O aluno ou responsável deve informar previamente se utilizará o transporte.

**Origem:**  
Necessidade de utilizar a presença dos alunos para geração da rota diária.

**Stakeholders envolvidos:**  
Aluno, responsável e motorista.

**Condição:**  
Aplicada antes do início previsto da rota.

**Regra:**  
O aluno ou responsável poderá confirmar a utilização do transporte
até 30 minutos antes do horário previsto de saída do motorista.

Caso não exista confirmação dentro desse prazo, o aluno será considerado ausente.

**Exceções:**  
Nenhuma identificada.

**Dados envolvidos:**  
Aluno, data, horário previsto de saída e status de presença.

**Prioridade:**  
Alta

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-004, RF-007

**Observações:**  
Nenhuma.

---

## RN-005 — Roteirização baseada nas presenças

**Título:**  
Geração da rota diária conforme alunos confirmados.

**Descrição:**  
A rota utilizada pelo motorista pode variar diariamente de acordo com
os alunos que utilizarão o transporte.

**Origem:**  
Objetivo do produto de reduzir deslocamentos desnecessários e otimizar a rota.

**Stakeholders envolvidos:**  
Motorista, aluno, responsável e empresa de transporte.

**Condição:**  
Aplicada durante a geração ou recálculo da rota.

**Regra:**  
Na geração inicial, a rota deve ser calculada considerando apenas os alunos
que confirmaram presença dentro do prazo estabelecido e a localização inicial
identificada do motorista.

Nos recálculos realizados durante o trajeto, deve ser considerada a localização
atual da van.

Alunos considerados ausentes não devem gerar pontos de parada.

**Exceções:**  
Caso nenhum aluno tenha presença confirmada, nenhuma parada de aluno
deverá ser incluída na rota.

**Dados envolvidos:**  
Alunos confirmados, pontos de parada, localização inicial do motorista, localização atual da van e rota.

**Prioridade:**  
Alta

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-004, RF-007, RF-008

**Observações:**  
Nenhuma.

---

## RN-006 — Cancelamento da utilização do transporte

**Título:**  
Cancelamento da presença.

**Descrição:**  
O aluno ou responsável pode informar que não utilizará mais o transporte,
mesmo após ter confirmado presença, desde que o embarque ainda não tenha
sido registrado.

**Origem:**  
Necessidade de permitir alterações decorrentes de imprevistos.

**Stakeholders envolvidos:**  
Aluno, responsável e motorista.

**Condição:**  
Aplicada quando já existe uma confirmação de presença.

**Regra:**  
O aluno ou responsável poderá cancelar a utilização do transporte a qualquer
momento antes do registro de embarque.

Após o cancelamento, o aluno deverá ser considerado ausente.

**Exceções:**  
Nenhuma identificada.

**Dados envolvidos:**  
Aluno, presença, data e horário do cancelamento.

**Prioridade:**  
Alta

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-005, RF-006, RF-008

**Observações:**  
Nenhuma.
---

## RN-007 — Notificação de cancelamento

**Título:**  
Notificação do motorista após cancelamento.

**Descrição:**  
Alterações na participação de um aluno na rota devem ser comunicadas ao motorista.

**Origem:**  
Necessidade de manter o motorista atualizado sobre mudanças na rota.

**Stakeholders envolvidos:**  
Motorista, aluno e responsável.

**Condição:**  
Aplicada sempre que uma presença confirmada for cancelada.

**Regra:**  
Quando o aluno ou responsável cancelar a utilização do transporte,
o motorista responsável pela rota deverá ser notificado.

**Exceções:**  
Nenhuma identificada.

**Dados envolvidos:**  
Aluno, motorista, rota e cancelamento.

**Prioridade:**  
Alta

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-006

**Observações:**  
Nenhuma.
---

## RN-008 — Recálculo da rota após cancelamento

**Título:**  
Atualização da rota após alteração de presença.

**Descrição:**  
A rota deve refletir alterações ocorridas depois de sua geração.

**Origem:**  
Roteirização dinâmica do VanTrack.

**Stakeholders envolvidos:**  
Motorista, aluno e empresa de transporte.

**Condição:**  
Aplicada quando um aluno presente na rota cancela a utilização do transporte.

**Regra:**  
Após o cancelamento, o ponto correspondente ao aluno deverá ser removido
e a rota deverá ser recalculada considerando os alunos restantes.

**Exceções:**  
Se não houver mais alunos confirmados, a rota não deverá possuir paradas de alunos.

**Dados envolvidos:**  
Aluno, pontos de parada, rota e localização atual da van.

**Prioridade:**  
Alta

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-008

**Observações:**  
Nenhuma.
---

## RN-009 — Vínculo obrigatório entre aluno e responsável

**Título:**  
Vínculo do aluno menor de idade com responsável.

**Descrição:**  
Todo aluno menor de idade cadastrado no VanTrack deve estar vinculado a pelo menos um responsável.

**Origem:**  
Modelo de usuários do VanTrack e necessidade de controle dos dados de menores.

**Stakeholders envolvidos:**  
Aluno, responsável e empresa de transporte.

**Condição:**  
Aplicada durante o cadastro e utilização do sistema por alunos menores de idade.

**Regra:**  
Um aluno menor de idade não poderá utilizar o sistema sem possuir pelo menos um responsável vinculado.

**Exceções:**  
Alunos maiores de idade poderão utilizar o sistema sem responsável obrigatório.

**Dados envolvidos:**  
Aluno, responsável e vínculo responsável-aluno.

**Prioridade:**  
Crítica

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-001, RF-011, RNF-002

**Observações:**  
Nenhuma.
---

## RN-010 — Confirmação de embarque e desembarque

**Título:**  
Registro obrigatório de embarque e desembarque.

**Descrição:**  
A utilização do transporte por um aluno deve possuir registros de embarque e desembarque.

**Origem:**  
Necessidade de informar aos responsáveis a situação do aluno durante o transporte.

**Stakeholders envolvidos:**  
Motorista, aluno e responsável.

**Condição:**  
Aplicada aos alunos presentes na rota do dia.

**Regra:**  
O motorista deverá confirmar o embarque e o desembarque de cada aluno que utilizar o transporte.

**Exceções:**  
Alunos considerados ausentes não devem possuir registros de embarque ou desembarque naquele trajeto.

**Dados envolvidos:**  
Aluno, motorista, rota, horário de embarque e horário de desembarque.

**Prioridade:**  
Alta

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-009, RF-010, RF-011, RNF-005

**Observações:**  
Nenhuma.
---

## RN-011 — Sequência de embarque e desembarque

**Título:**  
Desembarque condicionado ao embarque.

**Descrição:**  
O registro das etapas do transporte deve respeitar a sequência da utilização da van.

**Origem:**  
Fluxo de acompanhamento do aluno.

**Stakeholders envolvidos:**  
Motorista, aluno e responsável.

**Condição:**  
Aplicada no registro do desembarque.

**Regra:**  
O desembarque de um aluno somente poderá ser confirmado caso exista um embarque previamente registrado para o mesmo trajeto.

**Exceções:**  
Nenhuma identificada.

**Dados envolvidos:**  
Aluno, embarque, desembarque e rota.

**Prioridade:**  
Alta

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-010, RNF-005

**Observações:**  
Nenhuma.

---

## RN-012 — Motorista ativo da van

**Título:**  
Vínculo entre van e motorista responsável.

**Descrição:**  
Cada van em operação deve possuir um motorista responsável identificado.

**Origem:**  
Modelo de dados do VanTrack.

**Stakeholders envolvidos:**  
Motorista e empresa de transporte.

**Condição:**  
Aplicada enquanto uma van estiver em operação.

**Regra:**  
Uma van não poderá possuir mais de um motorista ativo simultaneamente.

**Exceções:**  
A troca de motorista é permitida desde que o vínculo anterior seja encerrado antes da ativação do novo motorista.

**Dados envolvidos:**  
Van, motorista e período do vínculo (início e fim).

**Prioridade:**  
Média

**Status:**  
Proposto

**Requisitos relacionados:**  
RF-002, RF-007, RF-012, RF-014

**Observações:**  
Nenhuma.

## RN-013 — Restrição de Acesso ao Chat por Vínculo

**Título:**
Chat restrito por vínculo motorista–responsável.

**Descrição:**
A comunicação via chat deve ocorrer apenas entre o motorista e os responsáveis/alunos vinculados à mesma van.

**Origem:**
Necessidade de centralizar a comunicação entre motoristas e responsáveis, preservando privacidade entre famílias.

**Stakeholders envolvidos:**
Motorista, responsável e aluno.

**Condição:**
Aplicada sempre que uma conversa for iniciada ou uma mensagem enviada.

**Regra:**
O sistema não deve permitir que um responsável visualize ou envie mensagens em conversas de vans às quais seu(s) aluno(s) não estejam vinculados, nem visualizar o chat de outro responsável.

**Exceções:**
Avisos de atraso em massa são transmissões do motorista para todos os responsáveis da van, não configurando conversa privada entre responsáveis entre si.

**Dados envolvidos:**
Van, motorista, responsável, vínculo aluno–van, mensagens.

**Prioridade:**
Alta

**Status:**
Proposto

**Requisitos relacionados:**
RF-013

**Observações:**
Nenhuma.

## RN-014 — Comunicação de Atraso a Todos os Responsáveis da Van

**Título:**
Aviso de atraso geral.

**Descrição:**
Qualquer atraso relevante identificado pelo motorista, ou detectado automaticamente pelo sistema, deve ser comunicado a todos os responsáveis vinculados à van afetada.

**Origem:**
Enquadramento do Problema — imprevistos não comunicados com agilidade.

**Stakeholders envolvidos:**
Motorista, responsável, aluno e empresa de transporte.

**Condição:**
Quando o motorista aciona manualmente o aviso de atraso, ou quando o sistema detecta desvio significativo entre o horário previsto e o real.

**Regra:**
O sistema deve notificar simultaneamente todos os responsáveis com alunos ativos na rota da van afetada, informando o motivo (quando informado) e a nova previsão de chegada.

**Exceções:**
Atrasos inferiores a um limiar mínimo configurado (ex.: X minutos) não geram notificação, para evitar excesso de alertas.

**Dados envolvidos:**
Van, rota, motivo do atraso, nova previsão, lista de responsáveis afetados, limiar mínimo configurado.

**Prioridade:**
Alta

**Status:**
Proposto

**Requisitos relacionados:**
RF-012, RF-015

**Observações:**
Nenhuma.

## RN-015 — Operação Dependente de Conectividade

**Título:**
Dependência de conectividade para funcionalidades em tempo real.

**Descrição:**
As funcionalidades de tempo real do sistema dependem de conexão com a internet.

**Origem:**
Restrições do projeto (conectividade requerida para tempo real; modo offline completo está fora do escopo).

**Stakeholders envolvidos:**
Motorista, responsável, aluno e empresa de transporte.

**Condição:**
Aplicada a toda funcionalidade que dependa de dados em tempo real.

**Regra:**
Quando não houver conectividade, o sistema deve informar clara e imediatamente ao usuário que os dados exibidos podem estar desatualizados ou indisponíveis, nunca apresentando uma localização desatualizada como se fosse atual.

**Exceções:**
Check-ins podem ser registrados localmente no dispositivo do motorista e sincronizados na reconexão, sem caracterizar modo offline completo.

**Dados envolvidos:**
Status de conectividade, timestamp da última atualização de localização.

**Prioridade:**
Média

**Status:**
Proposto

**Requisitos relacionados:**
RF-002, RF-003, RF-009, RF-010, RF-012, RF-013

**Observações:**
Nenhuma.

## RN-016 — Autorização para Dados de Menores

**Título:**
Autorização do responsável legal para dados de alunos menores.

**Descrição:**
O tratamento de dados pessoais de alunos menores de idade requer autorização formal do responsável legal.

**Origem:**
Restrições do projeto — LGPD (dados de menores com autorização).

**Stakeholders envolvidos:**
Responsável legal, aluno e empresa de transporte.

**Condição:**
No cadastro do aluno e antes de qualquer coleta de dado pessoal ou de localização referente ao menor.

**Regra:**
O cadastro de um aluno identificado como menor de idade somente pode ser concluído e ativado no sistema após o registro da autorização do responsável legal.

**Exceções:**
Alunos maiores de idade dependem apenas do próprio consentimento, não desta autorização.

**Dados envolvidos:**
Aluno, indicador de menoridade, responsável legal, registro de autorização.

**Prioridade:**
Crítica

**Status:**
Proposto

**Requisitos relacionados:**
RF-016

**Observações:**
Nenhuma.
