# Python.Gama.Accenture
Exercício de revisão

## Questão! 
![Questão](https://github.com/gabieng/Python.Gama.Accenture/blob/main/image.png)
![Questão](https://github.com/gabieng/Python.Gama.Accenture/blob/main/image%20(1).png)

## Código:
caixinhas = {}

def add_caixinha():
    while True:
        nome_caixinha = input("Qual o nome da caixinha? ")
        if nome_caixinha == "":
            print("O nome da caixinha não pode ser vazio. Por favor, tente novamente.")
            continue
        if nome_caixinha in caixinhas:
            print("Esta caixinha já existe. Tente novamente.")
            continue
        break
    while True:
        valor_caixinha = float(input("Digite o valor inicial da caixinha: "))
        if valor_caixinha < 0:
            print("O valor da caixinha não pode ser negativo. Por favor, tente novamente.")
            continue
        break
    
    caixinhas[nome_caixinha] = valor_caixinha
    print(f"O valor: {nome_caixinha}, foi adicionado com sucesso!")
    

def add_balance():
    nome_caixinha = input("Qual o nome da caixinha? ")
    if nome_caixinha not in caixinhas:
        print("This box does not exist. Please try again.")
        return
    
    while True:
        valor_saldo = float(input("Enter the value to be added: "))
        if valor_saldo < 0:
            print("O valor não pode ser negativo. Por favor, tente novamente.")
            continue
        break
    
    caixinhas[nome_caixinha] += valor_saldo
    print(f"O valor foi adicionado com sucesso à caixinha {nome_caixinha}!")
    
def remove():
    nome_caixinha = input("Qual o nome da caixinha para fazer a retirada? ")
    if nome_caixinha not in caixinhas:
        print("This box does not exist. Please try again.")
        return
    
    saldo_total = sum(caixinhas.values())
    valor_remover = float(input("Qual o valor que deseja remover? "))
    if valor_remover < 0:
        print("O valor não pode ser negativo. Por favor, tente novamente.")
        return
    if valor_remover > caixinhas[nome_caixinha]:
        print("Este valor não pode ser removido, pois não tem saldo suficiente.")
        return
    
    caixinhas[nome_caixinha] -= valor_remover
    print(f"O valor de {valor_remover:.2f} foi removido com sucesso da caixinha {nome_caixinha}!")


def display_balance():
    saldo_total = sum(caixinhas.values())
    print(f"O saldo total é: R$ {saldo_total:.2f}")
    
    
def menu():
    print("-----Planejamento Financeiro-----")
    while True:
        opcao = input("Escolha a atividade: adicionar, saldo, retirar e sair \n").lower()
        
        if opcao == "adicionar":
            add_caixinha()
        elif opcao == "saldo":
            display_balance()
        elif opcao == "retirar":
            remove()
        elif opcao == "sair":
            print("fechando o programa...")
            break
        else:
            print("Opção inválida, por favor, tente novamente.")


menu() 
