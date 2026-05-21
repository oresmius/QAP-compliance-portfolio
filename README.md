# QAP - Sistema de Compliance e PLD/FT

## Visão Geral e Motivação
O **QAP** é um sistema de compliance com arquitetura desktop (compatível com Linux e Windows), desenvolvido nativamente em Kotlin e Java, utilizando JavaFX para a interface gráfica.

Sua construção foi motivada pela necessidade de atender de forma rigorosa às exigências do Banco Central do Brasil sobre Prevenção à Lavagem de Dinheiro e Financiamento ao Terrorismo (PLD/FT), além de práticas de *Know Your Customer* (KYC) — com destaque para a aderência à **Circular BCB nº 3.978/2020** e à **Carta Circular BCB nº 4.001/2020**.

Atualmente, há uma lacuna tecnológica crônica no mercado brasileiro: as soluções de prateleira existentes possuem custos de licenciamento exorbitantes e são superdimensionadas para a realidade de instituições financeiras do **segmento S5**. O QAP foi projetado especificamente para preencher essa lacuna, oferecendo um processamento eficiente, robusto e enxuto, perfeitamente adequado ao volume operacional dessas empresas, sem abrir mão do estrito rigor regulatório.

---

## Funcionalidades em Desenvolvimento

- [x] **Autenticação e Gestão de Credenciais**
  Implementação do algoritmo **Argon2id** para o *hashing* seguro e armazenamento de senhas. A escolha garante proteção no estado da arte contra ataques de força bruta e análise de canais laterais (*side-channel attacks*), alinhando o sistema às diretrizes modernas de segurança da informação.

- [x] **Controle de Acesso Baseado em Papéis (RBAC)**
  Arquitetura estruturada para garantir a segregação segura de funções dentro do ambiente operacional. O módulo gerencia com rigor a divisão entre:
  * **Administradores:** Com privilégios totais de gestão de contas (criar, promover, rebaixar e inativar usuários).
  * **Usuários Operacionais:** Com acessos restritos exclusivamente às ferramentas de produção e análise, sem privilégios administrativos.

- [x] **Auditoria e Integridade de Dados (KYC)**
  * Rotinas para varredura e validação de integridade no banco de dados, identificando de forma proativa campos inconsistentes, mal formatados ou incompletos.
  * Sistema de rastreamento de ciclo de vida cadastral, gerando relatórios gerenciais periódicos sobre cadastros vencidos e emitindo alertas preditivos para documentações prestes a expirar (prazo de validade anual).

---

## Funcionalidades futuras.

- [ ] **Ingestão de Dados e Listas Restritivas (Batch Processing)**
  Desenvolvimento de *parsers* customizados em Kotlin para a importação e leitura local de arquivos estruturados nos formatos XML e CSV. Essa abordagem offline elimina a dependência de APIs externas de terceiros, garantindo resiliência operacional e maior velocidade no cruzamento da base de clientes com as listas de sanções da **ONU** e de **Pessoas Politicamente Expostas (PEP)** para fluxos de Diligência Reforçada (*Enhanced Due Diligence - EDD*).

- [ ] **Monitoramento Dinâmico (Caso de Uso em Destaque)**
  O sistema implementará um *Rule Engine* especializado na mitigação de riscos e prevenção a fraudes em operações de crédito e antecipação de recebíveis.
  * **Análise de Lastro e Capacidade Operacional:** Algoritmos desenvolvidos em Kotlin focados na identificação de picos anômalos de faturamento. O motor de regras emitirá alertas automáticos quando o volume de duplicatas descontadas por um cliente (como do setor de manufatura/confecção) ultrapassar abruptamente a capacidade produtiva ou financeira declarada durante a etapa de *onboarding* (KYC).

---

## Por que Kotlin? (Além do Android)

Embora o Kotlin seja amplamente consolidado como a linguagem oficial para o desenvolvimento mobile Android, vem tornando-se também uma ferramenta de propósito geral de altíssimo nível para aplicações corporativas na JVM (Backend e Desktop). A escolha do Kotlin como linguagem central do QAP fundamenta-se em três pilares:

1. **Segurança e Robustez (Null Safety):** Em arquiteturas de compliance, falhas em tempo de execução podem gerar omissões graves de monitoramento. O sistema de tipos do Kotlin mitiga nativamente o risco de *NullPointerExceptions*, garantindo esteiras de triagem previsíveis e tolerantes a falhas estruturais.
2. **Sintaxe Concisa e Foco no Domínio:** A expressividade da linguagem permite traduzir as regras complexas estabelecidas na Carta Circular BCB nº 4.001/2020 em código limpo, declarativo e de fácil manutenção, simplificando processos de auditoria interna e externa.
3. **Interoperabilidade Total com a JVM:** O Kotlin possui compatibilidade bidirecional de 100% com o ecossistema Java. Essa característica viabiliza o uso do **JavaFX** para a construção de uma interface desktop rica, performática e multiplataforma, combinando a engenharia moderna do Kotlin com a maturidade de componentes visuais Java.
