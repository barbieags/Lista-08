Implemente uma classe Empregado com os seguintes atributos: nome, idade e salario. Crie os métodos promover(), aumentarSalario(), demitir() e fazerAniversario() com as seguintes regras:
Regras dos Métodos:
Todos os atributos devem ser privados e os métodos públicos.
 Você deve implementar métodos get e set para todos os atributos, independentemente do uso.
 Implementar método toString.
promover()
A promoção só poderá ser realizada se o funcionário tiver mais de 18 anos.
A promoção resultará em um aumento de 25% no salário, utilizando o método aumentarSalario().
aumentarSalario()
Deve receber um percentual de aumento como parâmetro.
Deve realizar o aumento do salário do funcionário de acordo com o percentual informado.
demitir()
Deve receber um motivo como parâmetro (1, 2 ou 3):
1: Justa causa.
2: Decisão do empregador.
3: Aposentadoria.
Se o motivo for decisão do empregador, o empregado deverá receber uma multa de 40% do salário (realizar este cálculo e informar).
Se o motivo for justa causa, o funcionário deverá cumprir aviso prévio.
Se o motivo for aposentadoria, o salário de aposentadoria deve ser calculado conforme a tabela do INSS abaixo:
Salário entre 1000 e 2000 reais: receberá 1500 reais.
Salário entre 2000 e 3000 reais: receberá 2500 reais.
Salário entre 3000 e 4000 reais: receberá 3500 reais.
Salário acima de 4000 reais: receberá 4000 reais.
fazerAniversario()
Aumenta a idade do empregado em 1 ano.
Crie uma classe Principal com um menu interativo para testar a classe Empregado. O menu deve permitir ao usuário escolher as seguintes opções para manipular uma lista de empregados:
Criar novo empregado
Promover empregado
Aumentar salário do empregado
Demitir empregado
Fazer aniversário do empregado
Mostrar detalhes dos empregados
Sair
