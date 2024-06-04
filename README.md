Classe conta 
A classe conta deve ter:

saldo;
número;
agência;
cliente;
e histórico;
todos como atributos da classe e eles são privados (sinal de menos)
4 métodos:
saldo - não recebe nenhum argumento ele retorna float;
nova conta - é um método que cria uma conta (método de fábrica) então ele vai receber um cliente e o número da conta que pode ser um temporário, e tem retornar o objeto contra;
a operação de sacar - recebe um valor que é float e retorna um boleano;
e o depositar recebe um valor que é float e retorna boleano, para que se a operação aconteceu com sucesso ou falha retorna True se deu certo sacar, e caso se não depositar retorna falso, se deu errado e não depositar, por falso se deu errado também.
Conta corrente com herança
A Conta ela tem uma classe filha, então aqui a conta corrente estende a conta porque é uma classe do tipo conta, então ela tem tudo que a conta tem mais dois atributos que seriam: o limite e o limite de saques.

Atributo Histórico
Ainda continuando na conta temos o histórico, ele é um tipo de classe e essa classe é histórica, então uma conta tem um histórico, que pertence a uma conta.

Interface Transação
O histórico tem um método que é adicionar transação, ele também tem um argumento que são as transações, onde se depositando transações, que é do tipo transação, esta é uma interface, onde essa interface que seria a classe abstrata.
Aclasse abstrata Interface, é uma classe pai, então ela tem um método registrar que recebe uma conta, assim também temos duas classes que implementam essa interface.
As classe que implementam a abstrata da transação são: uma de depósito e a outra é a de saque, ambas tem os atributos do valor e consequentemente a implementação do método registrar.
Classe cliente
A classe cliente tem:

endereço;
e tem uma lista de contas - que é do tipo conta;
2 operações:
o primeiro é realizar transação - ele recebe dois atributos, que seria uma conta e a transação, onde a conta é do tipo conta e a transação é do tipo aqui da classe que estava na transação, então pode ser um saque, passar um depósito, mas a gente vai olhar ai para saber se temos um polimorfismo.
Adicionar conta - lembrando que o meu cliente pode ter várias contas, e com várias contas onde a conta é relacionada a um cliente e temos uma generalização.
Pessoa física
A classe pessoa física e é um tipo de cliente, ela tem:

CPF;
nome;
data de nascimento.
![diagrama-sistema-bancario](https://github.com/Clickylightiano/sistema-bancario/assets/169697198/1135cb72-bd57-4f5c-a4aa-0af0e07264ae)

_Desafio sistema bancário
Criar um sistema bancário com as operações:

sacar, depositar e visualizar extrato;
criar usuário e criar conta corrente.
Desafio
Fomos contratados por um grande banco para desenvolver o seu novo sistema. Esse banco deseja modernizar suas operações e para isso escolheu a linguagem Python.

Para a primeira versão do sistema devemos implementar apenas 3 operações: depósito, saque e extrato.

Para segunda versão precisamos deixar o código modularizado com funções e introduzir novas funcionalidades: criar usuário do banco e criar conta corrente, que vincula com o usuário.

Operação de depósito
Deve ser possível depositar valores positivos para a minha conta bancária. A v1 do projeto trabalha apenas com 1 usuário, dessa forma não precisamos nos preocupar em identificar qual é o número da agência e conta bancária. Todos os depósitos devem ser armazenados em uma variável e exibidos na operação de extrato.

Operação de saque
O sistema deve permitir realizar 3 saques diários com limite máximo de R$ 500,00 por saque. Caso o usuário não tenha saldo em conta, o sistema deve exibir uma mensagem informando que não será possível sacar o dinheiro por falta de saldo. Todos os saques devem ser armazenados em uma variável e exibidos na operação de extrato.

Operação de extrato
Essa operação deve listar todos os depósitos e saques realizados na conta. No fim da listagem deve ser exibido o saldo atual da conta. Se o extrato estiver em branco, exibir a mensagem: Não foram realizadas movimentações.

Os valores devem ser exibidos utilizando o formato R$ xxx.xx, exemplo:

1500.45 = R$ 1500.45

Exemplo de solução
# Criar 3 operações bancárias: depósito, saque e extrato.

# Menu pra escolher
menu = '''
Escolha:
  [d] depósitar
  [s] sacar
  [e] extrato
  [x] sair
'''
saldo = 0
limite_de_saque = 500
quantidade_de_saques = 3
while True:
    opcao = input(menu)
    if opcao == 'x': break
    # Depósito
    if opcao == 'd':
        valor = float(input('Digite o valor do depósito: R$ '))
        if valor > 0 :
            saldo += valor  # equivale a saldo + valor
            print(f'Depósito de R$ {valor} confirmado!\nSaldo: R$ {saldo}')
    # Saque
    if opcao == 's':
        valor = float(input('Digite o valor do saque: R$ '))
        if quantidade_de_saques > 0:
            if valor <= saldo:
                saldo -= valor
                print(f'Saque de R$ {valor} confirmado!\nSaldo: R$ {saldo}')
            else:
                print(f'Infelizmente não será possível sacar o dinheiro por falta de saldo\nSaldo: R$ {saldo}')
        else:
            print(f'Infelizmente não será possível sacar o dinheiro por limite de saques')

# Extrato

