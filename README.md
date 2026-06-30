# EDB I - Projeto da Unidade 2 e 3 

Simulação de um sistema de gerenciamento de senhas para atendimento hospitalar baseado no Protocolo de Manchester. Pacientes 
são classificados em 5 níveis de urgência e atendidos por filas encadeadas independentes, com regras de prevenção de inanição 
starvation prevention) para evitar que pacientes de menor prioridade fiquem esperando indefinidamente.

O Protocolo de Manchester classifica pacientes em cinco níveis de gravidade:

<img width="727" height="274" alt="image" src="https://github.com/user-attachments/assets/674d9533-7063-47c4-bc11-2fb0253472e3" />

Cada cor corresponde a uma fila FIFO independente. O atendente sempre busca o paciente mais grave disponível, mas com uma 
regra anti-inanição configurável: a cada N pacientes urgentes atendidos em sequência, um paciente de menor prioridade (Verde ou Azul) 
é atendido, garantindo que ninguém fique esperando para sempre.

O projeto simula a chegada aleatória de pacientes e mede o tempo de espera por nível de urgência, comparando o desempenho do sistema 
com prioridades contra uma fila FIFO tradicional sem distinção de gravidade.

# Estruturas de dados 

FilaEncadeada<T> — fila genérica implementada com ponteiros de cabeça e cauda, com enqueue e dequeue em O(1).
5 filas encadeadas — uma instância de FilaEncadeada<Paciente> por nível de triagem, organizadas em um array filas[5].

LogAtendimentos — lista encadeada que registra o histórico completo de atendimentos, com timestamp de entrada e saída de cada paciente.
Vetor de estatísticas — array de 5 posições com o tempo médio de espera por categoria, calculado a partir do log.

# Compilação 

Para compilar, va para a pasta do arquivo no terminal e execute o seguinte comando: 

> g++ -std=c++17 -Wall -o simulacao main.cpp simulacao.cpp

Esse comando gera o executável 'simulacao'

Para rodar, execute: 

> ./simulação (quantidade de pacientes) (limite de anti-inanição)

exemplo: ./simulação 1000 10 
