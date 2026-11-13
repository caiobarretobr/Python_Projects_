Projeto 1: Calculadora de terminal com histórico

O que faz: um programa em loop que pede dois números e uma operação (+, -, *, /, potência, resto), mostra o resultado e guarda um histórico das contas da sessão.

Conceitos testados: tipos e conversão, operadores, condicionais, while, funções com retorno, listas, f-strings.

Requisitos:

Menu com opções: calcular, ver histórico, limpar histórico, sair
Cada operação em uma função separada
Divisão por zero e entrada inválida (texto no lugar de número) não podem quebrar o programa
O histórico mostra as últimas 10 contas numeradas

Critérios de aceitação: o programa só termina quando escolho sair, nenhuma entrada errada gera traceback, e não há código repetido entre as operações.

Extras: operação com resultado anterior (“usar último resultado”); formatar números com 2 casas decimais.

Por onde começar: escreva primeiro as funções das operações, testando cada uma isolada, e só depois monte o menu.

Projeto 2: Jogo de adivinhação com placar

O que faz: o computador sorteia um número e o jogador tenta acertar, com dicas de “maior” ou “menor”. Há níveis de dificuldade e um placar dos melhores jogadores.

Conceitos testados: random, laços com break, dicionários, ordenação, strings, funções.

Requisitos:

3 níveis (faixas e número de tentativas diferentes)
Placar em um dicionário {nome: melhor_pontuação}, exibido ordenado
Validação de entrada (nada de letras, nada fora da faixa)
Pergunta se quer jogar de novo

Critérios de aceitação: a lógica do jogo fica separada da lógica de exibição (funções diferentes) e o placar só atualiza quando a pontuação melhora.

Extras: pontuação que considera tentativas e dificuldade; modo “o computador tenta adivinhar o meu número”.

Por onde começar: monte o jogo de uma rodada com um número fixo, sem sorteio, e só depois adicione os níveis e o placar.

Projeto 3: Agenda de contatos

O que faz: cadastra, busca, edita e remove contatos (nome, telefone, e-mail, categoria) mantidos em memória.

Conceitos testados: lista de dicionários, funções com parâmetros, list comprehension, busca e filtro, ordenação com key, tratamento de duplicatas.

Requisitos:

Cadastro com validação (telefone só com dígitos, e-mail com @)
Busca por trecho do nome, sem diferenciar maiúsculas de minúsculas
Listagem filtrada por categoria e ordenada por nome
Impedir contatos duplicados

Critérios de aceitação: nenhuma função mistura input com lógica de dados (funções que recebem parâmetros e retornam valores, sem input dentro) e há pelo menos 2 comprehensions bem aplicadas.

Extras: exportar a agenda formatada em texto; agrupar contatos por categoria com dicionário de listas.

Por onde começar: defina a estrutura de dados no papel (como é um contato, como é a agenda) antes de escrever qualquer função.

Projeto 4: Controle financeiro com arquivos

O que faz: registra receitas e despesas com data, valor, categoria e descrição, salva em arquivo e gera um resumo mensal.

Conceitos testados: leitura e escrita de JSON e CSV, datetime, try/except/finally, módulos próprios (import de arquivos seus), agregação de dados.

Requisitos:

Dados persistem entre execuções (JSON como armazenamento principal)
Exportação do extrato de um mês para CSV
Resumo mensal: total de receitas, despesas, saldo e gasto por categoria
Arquivo inexistente ou corrompido não derruba o programa
Código dividido em pelo menos 3 arquivos (ex.: armazenamento.py, relatorios.py, main.py)

Critérios de aceitação: fechar e abrir o programa mantém tudo, datas inválidas são rejeitadas com mensagem clara e o valor monetário não sofre erros visíveis de arredondamento.

Extras: filtro por intervalo de datas; meta de gasto mensal com alerta.

Por onde começar: faça primeiro só a persistência (salvar e carregar uma lista de dicionários), depois construa as funcionalidades em cima.

Projeto 5: Analisador de texto

O que faz: lê um arquivo .txt e gera estatísticas: total de palavras, palavras mais frequentes, tamanho médio das palavras, palavras únicas e linhas mais longas.

Conceitos testados: manipulação de strings, set, collections.Counter/defaultdict, pathlib, *args/**kwargs, comprehensions, funções reutilizáveis.

Requisitos:

Normalização do texto (minúsculas, remoção de pontuação)
Lista de “stop words” configurável para ignorar palavras como “de”, “a”, “o”
Uma função de relatório que aceita opções via **kwargs (ex.: top=10, min_tamanho=4)
Resultado salvo em um arquivo de saída

Critérios de aceitação: funciona com qualquer arquivo de texto, trata o caso de arquivo vazio ou inexistente, e a normalização está isolada em uma função própria.

Extras: comparar dois textos (palavras em comum e exclusivas usando operações de set); contar frases.

Por onde começar: teste a normalização com 3 ou 4 frases escritas à mão antes de ler arquivos.

Projeto 6: Sistema de estoque (OOP básica)

O que faz: controla produtos, quantidades e preços com entradas e saídas de estoque.

Conceitos testados: classes e objetos, atributos e métodos, encapsulamento (@property), __str__/__repr__, exceções customizadas, type hints, docstrings.

Requisitos:

Classe Produto (nome, preço, quantidade) com validações via @property (preço não negativo, quantidade inteira)
Classe Estoque que gerencia a coleção de produtos
Exceções próprias, como EstoqueInsuficienteError e ProdutoNaoEncontradoError
Relatório de produtos abaixo de um estoque mínimo e valor total em estoque
Persistência em JSON (converter objetos para dicionários e vice-versa)

Critérios de aceitação: nenhum atributo é alterado “por fora” de forma inválida, as exceções são levantadas e tratadas em lugares diferentes, e todos os métodos públicos têm type hints.

Extras: __eq__ e __lt__ para comparar produtos; @classmethod para criar produto a partir de dicionário.

Por onde começar: escreva só a classe Produto e teste no terminal interativo antes de criar Estoque.

Projeto 7: Banco simplificado (OOP avançada)

O que faz: simula contas bancárias com tipos diferentes, operações e extrato.

Conceitos testados: herança, polimorfismo, classes abstratas (abc), composição, super(), @staticmethod/@classmethod, persistência de objetos.

Requisitos:

Classe base abstrata Conta com depositar, sacar e extrato
Pelo menos duas subclasses (ex.: ContaCorrente com limite de cheque especial e ContaPoupanca com rendimento mensal), cada uma com regra de saque própria
Classe Cliente que possui várias contas (composição)
Classe Transacao registrando cada movimentação com data
Transferência entre contas, atômica (se falhar, nada muda)
Persistência em JSON de clientes, contas e transações

Critérios de aceitação: o mesmo código que percorre uma lista de contas chama sacar() sem saber o tipo (polimorfismo real), e não há if tipo == ... espalhado pelo código.

Extras: __iter__ no extrato; relatório de saldo total do cliente.

Por onde começar: desenhe o diagrama de classes (nome, atributos, métodos, relações) em papel antes de codar.

Projeto 8: Testes e refatoração do Projeto 7

O que faz: não é um programa novo. Você pega o Projeto 7 e o torna profissional.

Conceitos testados: pytest, fixtures simples, venv, pip, requirements.txt, PEP 8, docstrings, estrutura de pacote.

Requisitos:

Ambiente virtual criado e requirements.txt gerado
Mínimo de 15 testes cobrindo: depósito, saque válido, saque inválido, limites, transferência e persistência
Testes de exceções (pytest.raises)
Código reorganizado em pacote (banco/ com módulos separados)
Verificação de estilo com ruff ou flake8 sem erros

Critérios de aceitação: pytest passa limpo, um colega consegue clonar e rodar com 3 comandos, e você encontrou e corrigiu pelo menos 1 bug que os testes revelaram.

Extras: medir cobertura com pytest-cov e chegar a 85% ou mais.

Por onde começar: escreva os testes das funções mais simples primeiro (depósito) para pegar o ritmo.

Projeto 9: Gerenciador de tarefas CLI (integrador)

O que faz: um aplicativo de linha de comando para gerenciar tarefas com prioridade, prazo, tags e status.

Conceitos testados: tudo que veio antes, num único projeto estruturado.

Requisitos:

Interface via argparse (ex.: tarefas add "Estudar" --prioridade alta --prazo 2026-12-01, tarefas listar --status pendente, tarefas concluir 3)
OOP com pelo menos 3 classes (ex.: Tarefa, GerenciadorTarefas, Repositorio), com o repositório isolando a persistência
Persistência em JSON, com a camada de armazenamento trocável (sem a lógica de negócio saber como se salva)
Prazos com datetime, destacando tarefas vencidas
Filtros e ordenação por prioridade, prazo e tag
Tratamento de erros com mensagens amigáveis (sem traceback para o usuário)
Estrutura de pacote, venv, requirements.txt, README com exemplos de uso
Mínimo de 20 testes com pytest

Critérios de aceitação: instalação e uso documentados no README, cobertura de testes nas regras de negócio, código em PEP 8 com type hints e docstrings, e você consegue explicar cada decisão de design.

Extras: tarefas recorrentes; exportar relatório semanal em Markdown; um segundo repositório (SQLite) trocando só uma linha de código.

Por onde começar: escreva o README primeiro, descrevendo como o programa será usado. Isso força a definir a interface antes de codar.
