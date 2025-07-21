# Exercícios

---
### 1ª Escolha e apresente a definição de IA em pelo menos 2 das 4 correntes (pensando/agindo, humanamente/racionalmente)

> Sistemas que agem como seres humanos: "A arte de criar máquinas que executam funções que exigem inteligência
quando executadas por pessoas." (KURZWEIL, 1990). 

> Sistemas que atuam racionalmente: "A Inteligência Computacional é o estudo do projeto de agentes
inteligentes." (POOLE et al., 1998)

---
### 2ª É correto afirmar que um Agente racional sempre obterá as melhores soluções para um determinado problema? Justifique  a sua resposta.

> Não. Um agente racional busca tomar ações que maximizem sua medida de desempenho, porém nem sempre ele irá realizar a melhor ação. Racionalidade não é perfeição.

---
### 3º Definir agente inteligente.

> Um agente inteligente é aquele que busca tomar ações que maximizem sua medida de desempenho.
> Ele percebe o ambiente por meio de sensores e atua por meio de atuadores.

---
### 4ª Explicar as principais características e diferenças entre agentes reativos simples e agentes com estado interno.

> Um agente reativo simples executa uma ação tendo como base apenas a percepção atual. Por não ter nenhum tipo de memória ou estado interno, não consegue atuar com qualidade em ambientes parcialmente observáveis.

> O agente com estado interno, por sua vez, consegue atuar em ambientes parcialmente observáveis, pois ele pode armazenar a configuração do espaço não observável em seu estado interno.

---
### 5ª Comparar vantagens, desvantagens e classes de aplicações referentes a agentes reativos simples e agentes de aprendizagem.

> Agentes reativos simples mapeiam a percepção atual para uma ação. Porém, por não terem nenhum tipo de memória ou estado interno, não conseguem atuar com qualidade em ambientes parcialmente observáveis.

> Agentes com aprendizagem, por sua vez, conseguem atuar em ambientes desconhecidos, pois possuem a capacidade de entender a configuração daquele ambiente e de se adaptar a ele. Logo, é mais flexível.

---
### 6ª Explique e exemplifique quais as possíveis formas que um agente de aprendizagem pode adquirir conhecimento.

> Aprendizado Supervisionado: O Aprendizado Supervisionado é uma abordagem em que o algoritmo é treinado com um conjunto de dados rotulados, ou seja, dados que já possuem uma resposta correta. O objetivo é que o modelo aprenda a mapear as entradas para as saídas corretas.

> Aprendizado Não Supervisionado: No Aprendizado Não Supervisionado, o algoritmo é alimentado com um conjunto de dados não rotulados e é responsável por encontrar padrões e estruturas intrínsecas nos dados. Ao contrário do aprendizado supervisionado, não há respostas corretas fornecidas durante o treinamento.

> Aprendizado por Reforço: O Aprendizado por Reforço é uma abordagem que se baseia no conceito de recompensas e punições. O algoritmo aprende por meio da interação com um ambiente dinâmico, onde ele executa ações e recebe recompensas ou punições com base no desempenho. O objetivo é que o modelo aprenda a tomar decisões que maximizem a recompensa ao longo do tempo. Essa técnica é muito utilizada em jogos, robótica e sistemas de recomendação.

---
### 7ª Apresente um exemplo de problema em que o ambiente do agente possa ser classificado como estocástico, dinâmico, sequencial, multi-agente, parcialmente observável.

> Direção de Táxi.

> O ambiente de direção de táxi é estocástico porque há incertezas no trânsito, clima e comportamento dos passageiros; dinâmico, pois o mundo muda independentemente das ações do táxi, com outros veículos e eventos externos em constante movimento; sequencial, já que decisões atuais afetam diretamente as próximas etapas do trajeto; multi-agente, pois envolve a interação com outros motoristas, pedestres e passageiros, todos com objetivos próprios; e parcialmente observável, porque o táxi não tem acesso completo a todas as informações do ambiente, como congestionamentos futuros, acidentes ou intenções dos demais agentes.

---
### 8ª Apresente um exemplo de problema em que o ambiente do agente possa ser classificado como determinístico, estático, episódico, simples-agente, totalmente observável. 

> Classificação de Imagens.

> A tarefa de classificação de imagens se dá em um ambiente determinístico, pois a mesma imagem sempre leva à mesma resposta, sem elementos de aleatoriedade; estático, já que a imagem não muda durante o processamento e o ambiente permanece inalterado; episódico, porque cada imagem é analisada de forma independente, sem relação com classificações anteriores ou futuras; simples-agente, pois apenas um agente realiza a tarefa sem interação com outros; e totalmente observável, uma vez que toda a informação necessária para a decisão está contida na própria imagem, não havendo dados ocultos ou inacessíveis ao agente.

---
### 9ª Em qual destes ambientes um agente de resolução de problemas teria maior facilidade em operar: um ambiente totalmente observável ou um ambiente parcialmente observável? Justifique sua resposta. 

> Um agente de resolução de problemas teria maior facilidade em operar em um ambiente totalmente observável, pois nele todas as informações relevantes para a tomada de decisão estão disponíveis a qualquer momento. Isso permite que o agente conheça completamente o estado atual do ambiente, sem incertezas ou necessidade de inferência sobre partes ocultas.
