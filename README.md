# Bipedal-walker-Reinforcement-Leraning
# Bipedal-walker
Este repositório contém o projeto desenvolvido no âmbito da unidade curricular de Introdução aos Sistemas Inteligentes e Autónomos. O objetivo principal foi aplicar técnicas de Reinforcement Learning (RL) para resolver o ambiente BipedalWalker-v3 e analisar a capacidade de adaptação dos agentes a uma alteração estrutural no ambiente (simulação de lesão).
Autores:Francisca CerqueiraIara FerreiraRodrigo Simões
**Visão Geral do Projeto**
O trabalho foi dividido em três marcos principais, focados na customização do ambiente, implementação e treino de agentes com Stable-Baselines3, e análise comparativa de resultados.
1. Customização do Ambiente
Ambiente Base: BipedalWalker-v3 (Box2D/Gymnasium).
Modificação Implementada: Criação do ambiente InjuredBipedalWalker.
Descrição: Foi introduzida uma "lesão" mecânica no robô, caracterizada por uma perda de 70% de potência nos motores da perna direita.
Objetivo: Testar a robustez dos algoritmos e forçar o agente a aprender uma marcha compensatória assimétrica.
Código: Disponível em my_envs/injured_bipedal.py.
3. Agente de Reinforcement Learning
Seleção de Algoritmos: Foram comparados quatro algoritmos: PPO, A2C, SAC e TD3.
Agente Selecionado: O TD3 (Twin Delayed DDPG) demonstrou o melhor desempenho e estabilidade nas experiências preliminares.
Tuning: Otimização de hiperparâmetros (Learning Rate, Gamma, Action Noise).A configuração vencedora para o ambiente original foi a variante "Míope" ($\gamma=0.98$), que atingiu uma pontuação média consistente de ~278 pontos.
5. Avaliação e Análise
Teste de Robustez: O agente treinado no ambiente saudável falhou ao ser transferido para o ambiente lesionado (queda de performance de ~278 para ~27 pontos), evidenciando a falta de generalização para falhas dinâmicas.
Re-treino no Ambiente Modificado: O treino direto no InjuredBipedalWalker permitiu ao agente aprender a não cair (estratégia de sobrevivência), mas com dificuldade em progredir rapidamente, resultando frequentemente em timeouts.
Conclusão: O agente desenvolveu uma marcha compensatória visível, sacrificando velocidade por estabilidade.

**Instalação e Utilização**
1.Pré-requisitos
Certifica-te de que tens o Python instalado (recomendado 3.8+).

2. Instalar dependências
Bash

**pip install -r requirements.txt**

3. Executar os Notebooks
A análise completa e o código de treino encontram-se nos Jupyter Notebooks. Podes executá-los sequencialmente:

01_exploracao.ipynb: Para visualizar o espaço de ações/observações.

02_selecao_e_tuning.ipynb: Para replicar a seleção do algoritmo TD3 e o tuning no ambiente saudável.

03_ambiente_modificado.ipynb: Para ver a implementação da "lesão", o treino no ambiente modificado e a comparação final (vídeos e gráficos).

4. Visualizar o Treino
Para visualizar as curvas de aprendizagem em tempo real ou a posteriori:
**tensorboard --logdir ./logs**

