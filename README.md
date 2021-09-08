# Batalha-Naval---Oficial
import random
 
x = int(input("Antes de embarcar nesta aventura em alto mar, escolha o comprimento do tabuleiro: "))
y = int(input("Antes de embarcar nesta aventura em alto mar, escolha a altura do tabuleiro: " ))
tabuleiro = [0] * y
mapa_do_tabuleiro = ["⛴"] * y
matriz_do_pânico =[]
mapa_do_tesouro = []
i = 0

destroyer= 1
cruzador = 2
fragata = 3
porta_aviões = 5
 
destroyer_bombardeia = 0
cruzador_bombardeia = 0
fragata_bombardeia= 0
porta_aviões_bombardeia = 0
 
def matriz_do_tabuleiro(bomba, ataque):
  i = 0
  while i < ataque:
    print (bomba[i])
    i = i + 1
 
def matriz_do_mapa_do_tesouro(bomba, ataque):
  i = 0
  while i < ataque:
    print (bomba[i])
    i = i + 1
 
while i < x:
  matriz_do_pânico.append(tabuleiro.copy())
  mapa_do_tesouro.append(mapa_do_tabuleiro.copy())
  i = i + 1
 
while destroyer_bombardeia < destroyer:
  linha = random.randint(0, x-1)
  pilar = random.randint(0, y-1)
  matriz_do_pânico[linha][pilar] = 1
  destroyer_bombardeia = destroyer_bombardeia + 1
 
while cruzador_bombardeia < cruzador:
  linha = random.randint(0 , x-1)
  pilar = random.randint(0 , y-1)
  while (matriz_do_pânico[linha][pilar] == 1):
    linha = random.randint(0, x-1)
    pilar = random.randint(0, y-1)
  matriz_do_pânico[linha][pilar] = 2
  cruzador_bombardeia = cruzador_bombardeia + 1
 
while fragata_bombardeia < fragata :
  linha = random.randint(0, x-1)
  pilar = random.randint(0, y-1)
  while (matriz_do_pânico[linha][pilar] == 1) or (matriz_do_pânico[linha][pilar] == 2): 
    linha = random.randint(0, x-1)
    pilar = random.randint(0, y-1)
  matriz_do_pânico[linha][pilar] = 3
  fragata_bombardeia  = fragata_bombardeia  + 1
 
while porta_aviões_bombardeia < porta_aviões:
  linha = random.randint(0, x-1)
  pilar = random.randint(0, y-1)
  while (matriz_do_pânico[linha][pilar] == 1) or (matriz_do_pânico[linha][pilar] == 2) or (matriz_do_pânico[linha][pilar] == 3):
    linha = random.randint(0, x-1)
    pilar = random.randint(0, y-1)
  matriz_do_pânico[linha][pilar] = 5
  porta_aviões_bombardeia = porta_aviões_bombardeia + 1

print("") 
print("Bem-vindo ao jogo de Batalha Naval!")
print("")
print("REGRAS:")
print(f"A) A dimensão do tabuleiro tem tamanho {x}x{y}, por isso escolha a linha e o pilar de acordo com o mapa.")
print("B) Apenas 2 jogadores poderam participar desta batalha mortal.")
print("C) Voce pode, em cada partida:")
print("   -Ganhar 1 ponto, ao acertar um destroyer.")
print("   -Ganhar 2 pontos, ao acertar um cruzador.")
print("   -Ganhar 3 pontos, ao acertar um fragata.")
print("   -Perder 5 pontos, ao acertar um porta-aviões.")
print("")
print("DICAS:")
print("01 - O jogo terá 4 embarcações, com uma em especial que pode ser uma armadilha em alto mar.")
print("02 - Deve-se derrubar as embarcações, por meio de um ataque(bombas). No entanto, lembre-se: Se acertar o coração da frota, pode ser o seu fim!")
print("03 - Ganha o jogador que derrubar todas as embarcações primeiro.")
print("04 - Em meio a está emocionante batalha em alto mar, o vencedor irá ganhar cerca de 1 milhão de doses da vacina CORONAVAC!")
print("-"*15)
 
  
def batalha_naval(L, C):
  batalha_naval_play_01 = 0
  if matriz_do_pânico[L-1][C-1] == 0:
    print('O tripulante mirou na agua!')
    matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = "🌊"
    mapa_do_tesouro[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = "🌊"
  elif matriz_do_pânico [L-1][C-1] == 1:
    print("Lacrou! Voce abateu um destroyer!")
    batalha_naval_play_01 = batalha_naval_play_01 + 1
    matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = "💣"
    mapa_do_tesouro[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = "💣"
  elif matriz_do_pânico[L-1][C-1] == 2:
    print("Lacrou! Voce abateu um cruzador!")
    batalha_naval_play_01 = batalha_naval_play_01 + 2
    matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = "💣"
    mapa_do_tesouro[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = "💣"
  elif matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] == 3:
    print("Lacrou! Voce acertou um fragata!")
    batalha_naval_play_01 = batalha_naval_play_01 + 3
    matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = "💣"
    mapa_do_tesouro[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = "💣"
  elif matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] == 5:
    print("Opss!! Voce abateu um porta-aviões, perdeu 5 pontos! ")
    batalha_naval_play_01 = batalha_naval_play_01 - 5
    matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = '☠️'
    mapa_do_tesouro[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = '☠️'
  elif matriz_do_pânico [linha_do_tabuleiro-1][pilar_do_tabuleiro-1] == '💣':
    print("Opss!Voce atirou no lugar errado! Passou a vez")
    print("Espere uma outra partida")
  elif matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] <= 0 and matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] >=10:
    print("Este direcionamento nao encontra-se no tabuleiro!")
    print("Voce perdeu a vez!")
  else:
    batalha_naval_play_01 = batalha_naval_play_01 + 0
  return(batalha_naval_play_01)
 

while True:
  plays = int(input("Quantos jogadores participarão da Batalha pela coronavac? "))
  if plays > 0 and plays < 3:
    play1 = input("Escolha um usuario para jogar - Moana, Bob Esponja, Aquaman, Poseidon: ")
    play2 = input("Escolha um usuario para jogar - Moana, Bob Esponja, Aquaman, Poseidon: ")
    break
  else:
    print("-"*30)
    print("*Selecione a quantidade de jogadores valida*")
    print("-"*30)
 
 
print("-"*30)
print("**PREPARE-SE PARA NAVEGAR, POIS O PÂNICO EM ALTO MAR ESTÁ PRESTES A COMEÇAR !**")
print("-"*30)


pontos_da_batalha_1= 0
pontos_da_batalha_2 = 0
destroyer_bombardeia = 1
cruzador_bombardeia = 2
fragata_bombardeia = 3


while True:
  print("")
  print(f"{play1}, é sua vez!")
  matriz_do_mapa_do_tesouro(mapa_do_tesouro, x)
  pilar_do_tabuleiro = int(input("Qual o pilar que voce quer jogar? "))
  linha_do_tabuleiro = int(input("Qual a linha que voce quer jogar? "))
  print(""*30)
  tripulante01 = int(batalha_naval(linha_do_tabuleiro,pilar_do_tabuleiro))
  matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = "💣"
  pontos_da_batalha_1 = pontos_da_batalha_1 + tripulante01
  if tripulante01 == 1:
    destroyer_bombardeia = destroyer_bombardeia - 1
  if tripulante01 == 2:
    cruzador_bombardeia = cruzador_bombardeia - 1
  if tripulante01 == 3:
    fragata_bombardeia = fragata_bombardeia - 1
  print(f"{play1} tem {pontos_da_batalha_1} pontos")
  print("")
  print("*"*30)
  if plays == 2:
    print("")
    print(f"{play2}, é sua vez!")
    matriz_do_mapa_do_tesouro(mapa_do_tesouro, x)
    pilar_do_tabuleiro = int(input("Qual o pilar que voce quer jogar? "))
    linha_do_tabuleiro = int(input("Qual a linha que voce quer jogar? "))
    print("-"*30)
    tripulante02 = int(batalha_naval(linha_do_tabuleiro, pilar_do_tabuleiro))
    matriz_do_pânico[linha_do_tabuleiro-1][pilar_do_tabuleiro-1] = "💣"
    pontos_da_batalha_2 = pontos_da_batalha_2 + tripulante02
    if tripulante02 ==1:
      destroyer_bombardeia = destroyer_bombardeia - 1
    if tripulante02 == 2:
      cruzador_bombardeia = cruzador_bombardeia - 1
    if tripulante02 == 3:
      fragata_bombardeia = fragata_bombardeia -  1
    print(f"{play2} tem {pontos_da_batalha_2} pontos")
    print("")
    print("*"*30)
  print(f"Destroyer {destroyer_bombardeia}")
  print(f"Cruzador {cruzador_bombardeia}")
  print(f"Fragata {fragata_bombardeia}")
  if destroyer_bombardeia == 0 and cruzador_bombardeia == 0 and fragata_bombardeia == 0:
    break


matriz_dos_tripulantes = [pontos_da_batalha_1, pontos_da_batalha_2]
valorDOganhador = 0 
listaDOganhador = 0 
valor_elevado_de_pontos = 0 
empate = 0
while valorDOganhador < len(matriz_dos_tripulantes):
  if matriz_dos_tripulantes[valorDOganhador] > valor_elevado_de_pontos:
    valor_elevado_de_pontos = matriz_dos_tripulantes[valorDOganhador]
    listaDOganhador = valorDOganhador
  elif matriz_dos_tripulantes[valorDOganhador] == valor_elevado_de_pontos:
    empate = 1
