# Criando-um-sistema-banc-rio-com-python-Fabio
#Desafio-DIO

##

menu = """"
[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair
"""

saldo = 0
limite_saque = 500
saque_valor = 0
extrato = ""
numero_saques = 0
N_limite_saques = 3

while True:

    operacao = input(menu)
    

    if operacao == "d":

        print("Operação de Depósito selecionada.")
        deposito_valor = float(input("Insira o valor do deposito: "))

        if deposito_valor  > 0:

            saldo += deposito_valor
            extrato += f"Depósito num valor de R${deposito_valor: .2f}\n"
            print(f"O valor depositado foi de R${deposito_valor}")
            print(f"O saldo atual da conta é de R${saldo}.")
            print("Voltando para o menu inicial da conta.")
            
        else:
            print("Valor inserido é inválido, tente novamente.")

    elif operacao == "s":
        print("Operação de Saque")

        saque_valor = float(input("Insira o valor do saque: "))
        saldo_excedido = (saque_valor > saldo)
        saque_limite_excedido = (saque_valor > limite_saque)
        n_saques_excedido = (numero_saques >= N_limite_saques)

        # if saque_valor <0:
        #     print("Operação falhou! Não é possível realizar este saque.")

        if saque_limite_excedido:
            print("O valor inserido é inválido! o valor do saque excede o limite.")
        
        elif saldo_excedido: 
            print("O valor inserido é inválido! Você não tem saldo suficiente.")

        elif n_saques_excedido: 
            print("Operação falhou! O número máximo de saques ja foi realizado.")


        elif saque_valor >0:

            saldo -= saque_valor
            print(f"O valor sacado foi de {saque_valor}")
            print(f"O saldo atual da conta é de R${saldo}.")
            print("Voltando para o menu inicial da conta.")
            extrato += f"Saque num valor de R${saque_valor: .2f}\n" 
            numero_saques += 1

        else:
            print("Operação falhou! O valor informado é inválido.")

    elif operacao == "e":
        print("Operação de Extrato.")
        print("==========EXTRATO==========")
        print(f"Operações realizadas: \n{extrato}")
        print("===========================")

    elif operacao == "q":
        print("Saindo da conta")

        break

    else:    
        print("Operação inválida, por favor selecione novamente a operação e dados desejados")
