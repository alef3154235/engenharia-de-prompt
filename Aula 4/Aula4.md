# Atividade-4-engenharia-de-prompt

Aqui está um exemplo de **Jogo da Velha simples feito em Python** para rodar no terminal.  
Ele permite dois jogadores alternando entre **X** e **O**.

---

## 🎮 Código do Jogo da Velha

```python
# Jogo da Velha no terminal

tabuleiro = [" " for _ in range(9)]

def mostrar_tabuleiro():
    print()
    print(tabuleiro[0] + " | " + tabuleiro[1] + " | " + tabuleiro[2])
    print("--+---+--")
    print(tabuleiro[3] + " | " + tabuleiro[4] + " | " + tabuleiro[5])
    print("--+---+--")
    print(tabuleiro[6] + " | " + tabuleiro[7] + " | " + tabuleiro[8])
    print()

def verificar_vitoria(jogador):
    combinacoes = [
        (0,1,2),(3,4,5),(6,7,8), # linhas
        (0,3,6),(1,4,7),(2,5,8), # colunas
        (0,4,8),(2,4,6)          # diagonais
    ]

    for a,b,c in combinacoes:
        if tabuleiro[a] == tabuleiro[b] == tabuleiro[c] == jogador:
            return True
    return False

def jogo():
    jogador = "X"

    for turno in range(9):
        mostrar_tabuleiro()

        posicao = int(input(f"Jogador {jogador}, escolha uma posição (1-9): ")) - 1

        if tabuleiro[posicao] == " ":
            tabuleiro[posicao] = jogador
        else:
            print("Posição ocupada! Tente novamente.")
            continue

        if verificar_vitoria(jogador):
            mostrar_tabuleiro()
            print(f"🎉 Jogador {jogador} venceu!")
            return

        jogador = "O" if jogador == "X" else "X"

    mostrar_tabuleiro()
    print("😐 Deu empate!")

jogo()
