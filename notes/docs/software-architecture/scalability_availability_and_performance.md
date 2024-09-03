# Escalabilidade, Disponibilidade e Desempenho

## Escalabilidade

A característica que permite o software crescer para lidar com maiores demandas de trabalho

Estratégias para tornar o software escalável:
- Arquitetura projetada para suportar aumento de demanda
- Seguir boas práticas de código
- Utilizar tecnologias modernas como Cloud Computing e Contêineres
- Banco de dados Escalável como NoSql e Cache
- Monitorar e otimizar

### Monitoração

Ferramentas:
- New Relic: análise de desempenho
- Nagios: monitoração de serviços de rede, open source e alertas
- Splunk: análise e inteligência de dados, pode ser usado para monitorar logs
- AppDynamics: monitoramento e análise de desempenho
- VisualVM: monitoramento de desempenho
- Zabbix: Ferramenta de software de código aberto para monitorar a infraestrutura de TI, como redes, servidores, máquinas virtuais e serviços em nuvem
- Prometheus com Grafana: Prometheus coleta métricas de utilização da plataforma, já o grafana exibe de forma mais confortável e configurável (UI)
  
### HealthCheck

Disponibilizar entrypoints para verificação da saúde do serviço, incluindo a esteira toda dele, como: verificar se o banco de dados está funcionando, cache e etc.

### Escalabilidade Horizontal vs Vertical

Horizontal: Capacidade de aumentar o número de instâncias (replicações) do serviço e continuar operando corretamente
Vertical: Capacidade de aumentar a disponibilidade de recursos computacionais para a mesma instância (memória, cpu e etc)

## Disponibilidade

Refere-se à capacidade de um sistema estar operacional a todo momento para que o usuário o opere
É medida em termos de tempo de atividade: tempo que está disponível VS tempo total

## Observabilidade

Capacidade do sistema de ser observável, o que permite detectar anomalias e agir proativamente na resolução.

## Desempenho

Capacidade do sistema em realizar as tarefas a qual se propõe a realizar em tempo hábil, conforme expectativa.
Pode ser medido como:
- Tempo de resposta
- Taxa de transferência
- Utilização de Recursos
- Confiabilidade
- Escalabilidade

## Cache

Para melhorar o desempenho do aplicativo, uma das estratégias é armazenar temporariamente o resultado de dados que levam um tempo maior para serem processados, diminuindo a carga de trabalho e retornando mais rapidamente.
Estratégias comuns:
- Cache de página inteira
- Cache de banco de dados
- Cache de imagem
- Cache de sessão
- Cache de CDN (rede de entrega de conteúdo)