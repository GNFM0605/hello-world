import random

def jogo_acerte_o_numero():
    # Gerando um número aleatório de 0 a 10
    numero_secreto = random.randint(0, 10)

    print("Bem-vindo ao jogo de Acerte o Número!")
    print("Tente adivinhar o número secreto de 0 a 10. Você tem 5 tentativas.")

    pontuacao_maxima = 100
    pontuacao_minima = 10

    # Loop para as tentativas
    for tentativa in range(1, 6):
        # Recebendo o palpite do usuário
        while True:
            try:
                palpite = int(input(f"Tentativa {tentativa}: Digite um número de 0 a 10: "))
                if palpite < 0 or palpite > 10:
                    raise ValueError("Número fora da faixa permitida!")
                break
            except ValueError as e:
                print(e)

        # Verificando se o palpite está correto
        if palpite == numero_secreto:
            if tentativa == 1:
                pontuacao = pontuacao_maxima
            elif tentativa == 5:
                pontuacao = pontuacao_minima
            else:
                pontuacao = pontuacao_maxima - (tentativa - 1) * (pontuacao_maxima - pontuacao_minima) / 4

            print(f"Parabéns! Você acertou o número secreto na {tentativa}ª tentativa!")
            print(f"Sua pontuação é: {pontuacao} pontos.")
            break
        else:
            if tentativa == 5:
                print("Game Over! O número secreto era:", numero_secreto)
            else:
                # Dando uma dica ao jogador
                if palpite < numero_secreto:
                    print("Tente um número maior.")
                else:
                    print("Tente um número menor.")

def novo_jogo():
    while True:
        jogo_acerte_o_numero()
        resposta = input("Deseja iniciar uma nova partida? (s/n): ").lower()
        if resposta != 's':
            print("Obrigado por jogar! Até mais!")
            break

novo_jogo()
