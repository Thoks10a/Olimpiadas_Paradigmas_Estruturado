
# Arremesso de peso – O/A atleta possui três arremessos. A posição na
# classificação é determinada pela distância obtida no maior arremesso válido;
# em, caso de empate, vale a segunda maior marca do atleta.

# • Ginástica Artística – O/A atleta recebe cinco notas de diferentes juízes e a nota
# mais baixa é excluída da somatória final das notas.


                                # Observações:

# • A competição será realizada entre apenas dois adversários;

# • Em C, Java e Python é necessário criar um menu com escolhas para as
# modalidades e as entradas dos dados (arremessos e notas);

# • Em Scheme ou Haskell, a nota será dada sobre as funções criadas para decidir
# quem é o/a vencedor(a).


import numpy as np
# Apresentação

print()
print('*'*100)
print(' '*35+'BEM VINDO AS OLIMPIADAS')
print('*'*100)

# Escolha da modalidade
while True:
    print('*'*100)
    escolha = int(input("Digite o valor de escolha: \n - 1 para Arremesso de Peso \n - 2 para Ginástica Artística \n - 0 para Sair \n "))

    # Escolha de saida
    if(escolha == 0):
        print()
        print('Saindo em 3...')
        print('Saindo em 2...')
        print('Saindo em 1...')
        print()
        break
    
    else:
        # Verificação de oscolha entre 2 e 1 ou 0 para sair
        if(escolha != 1 and escolha != 2):
           print('\n \033[0;31mPorfavor escolha entre 1 e 2 para as modalidades da olimpiada, caso queira sair digite 0! \n \033[m')
        
        # Modalidade de arremesso
        if (escolha == 1):
            print('*'*100)
            print('Vamos entrar com os dados dos competidores: \n')
            print()
            # pontos dos competidores
            jogador1_pontos = []
            jogador2_pontos = []
            # validação dos nomes
            while True:
                jogador1_nome = input('Digite  o nome do primeiro competidor:      ')
                print()
                jogador2_nome = input('Digite  o nome do segundo competidor:       ')
                print()
                if jogador1_nome.isdigit() == True or jogador2_nome.isdigit() == True:
                    print('\033[0;31mPorfavor digite apenas letras para o nome dos competidores! \n \033[m')
                if jogador1_nome == jogador2_nome:
                    print('\033[0;31mPorfavor use nomes diferentes para os competidores! \n \033[m')
                else:
                    if jogador1_nome.isdigit() == False and jogador2_nome.isdigit() == False:
                        break
            
            print('\nCompetidores registrados !\n')
            print()
            print('                 '+'    '+' Competidor 1: '+'('+jogador1_nome+')'+'    '+' Competidor 2: '+'('+jogador2_nome+')'+'    '+'\n')
            print()
            print('*'*100)
            print()
            print(' '*100)
            # validação dos pontos dos competidores
            
            while True:
                
                try:
                    maybe = True
                    for cont  in range(0,3):
                        
                        print()
                        jogador1_pontos.append(float(input(f'\n Digite o valor de arremesso do(a) ( {jogador1_nome}  rodada {cont} ) :  ')))

                        print()
                        jogador2_pontos.append(float(input(f'\n Digite o valor de arremesso do(a) ( {jogador2_nome} rodada {cont}) :   ')))
                        
                            
                            
                # validação para não deixar entrar nenhum tipo de erro        
                
                except (Exception,ValueError):
                    print('\033[0;31mPorfavor digite apenas numeros inteiros para os pontos dos competidores que seja acima de zero! \n \033[m')
                    maybe = False
                
                if maybe == True:
                    if jogador1_pontos[0] < 0 or jogador1_pontos[1] < 0 or jogador1_pontos[2] < 0 or jogador2_pontos[0] < 0 or jogador2_pontos[1] < 0 or jogador2_pontos[2] < 0:
                        print('\033[0;31mPorfavor digite apenas numeros inteiros para os pontos dos competidores que seja acima de zero! \n \033[m')
                        maybe = False
                        jogador1_pontos = []
                        jogador2_pontos = []
                
                # saida do laço quando os vetores possuirem tamanho  = 3
                if maybe == True:
                    if len(jogador1_pontos) == 3 and len(jogador2_pontos) == 3:
                        break
            
            print()
            print()
            # printa os pontos de arremesso de cada competidor
            for c,i in enumerate(jogador1_pontos):
                c += 1
                print(f'Jogador *** {jogador1_nome} *** rodada {c} arremesso : {i}   ',end = '  ')
                # print(i)
            
            print()
            print()    
            
            for c,i in enumerate(jogador2_pontos):
                c += 1
                print(f'Jogador *** {jogador2_nome} ***  rodada {c} arremesso : {i}   ',end = '  ')
                # print(i)
            
            print()    
            print()
            print('\033[0;32mPARABENS! \n \033[m')
            print()
            print()
            # valida qual competidor é ganhou
            jogponto1 = max(jogador1_pontos,key=float)
            jogponto2 = max(jogador2_pontos,key=float)
            if(max(jogador1_pontos, key=float) > max(jogador2_pontos,key=float)):
                print(f'\033[0;32mParabens {jogador1_nome} você venceu as olimpiadas por {jogponto1}! \n \033[m')
            if(max(jogador1_pontos, key=float) < max(jogador2_pontos,key=float)):
                print(f'\033[0;32mParabens {jogador2_nome} você venceu as olimpiadas por {jogponto2}! \n \033[m')
            if(max(jogador1_pontos, key=float) == max(jogador2_pontos,key=float)):
                jogador1_pontos.remove(max(jogador1_pontos))
                jogador2_pontos.remove(max(jogador2_pontos))
                if(max(jogador1_pontos, key=float) > max(jogador2_pontos,key=float)):
                    print(f'\033[0;32mParabens {jogador1_nome} você venceu as olimpiadas por {jogponto1}! \n \033[m')
                if(max(jogador1_pontos, key=float) < max(jogador2_pontos,key=float)):
                    print(f'\033[0;32mParabens {jogador2_nome} você venceu as olimpiadas por {jogponto2}! \n \033[m')
                if(max(jogador1_pontos, key=float) == max(jogador2_pontos,key=float)):
                    jogador1_pontos.remove(max(jogador1_pontos))
                    jogador2_pontos.remove(max(jogador2_pontos))
                    if(max(jogador1_pontos, key=float) > max(jogador2_pontos,key=float)):
                        print(f'\033[0;32mParabens {jogador1_nome} você venceu as olimpiadas por {jogponto1}! \n \033[m')
                    if(max(jogador1_pontos, key=float) < max(jogador2_pontos,key=float)):
                        print(f'\033[0;32mParabens {jogador2_nome} você venceu as olimpiadas por {jogponto2}! \n \033[m')
        
        
        # Escolha 2     
                
        
        
        # Ginásticas Artísticas
        if (escolha == 2):
            print('*'*100)
            print('Vamos entrar com os dados dos competidores: \n')
            print()
            # Vetores para a entrada de pontos dos competidores
            jogador1_pontos = []
            jogador2_pontos = []
            # Nomes dos competidores / Validação dos nomes
            while True:
                jogador1_nome = input('Digite  o nome do primeiro competidor:      ')
                print()
                jogador2_nome = input('Digite  o nome do segundo competidor:       ')
                print()
                if jogador1_nome.isdigit() == True or jogador2_nome.isdigit() == True:
                    print('\033[0;31mPorfavor digite apenas letras para o nome dos competidores! \n \033[m')
                if jogador1_nome == jogador2_nome:
                    print('\033[0;31mPorfavor use nomes diferentes para os competidores! \n \033[m')
                else:
                    if jogador1_nome.isdigit() == False and jogador2_nome.isdigit() == False:
                        break
                
            # Saida dos nomes 
            print('\nCompetidores registrados !\n')
            print()
            print('                 '+'    '+' Competidor 1: '+'('+jogador1_nome+')'+'    '+' Competidor 2: '+'('+jogador2_nome+')'+'    '+'\n')
            print()
            print('*'*100)
            print()
            print(' '*100)
            # Laço para dar entrada de pontos = 5 
            while True:
                
                try:
                    maybe = True
                    for cont  in range(0,5):
                        
                        print()
                        jogador1_pontos.append(int(input(f'\n Digite a nota de ( {jogador1_nome}  rodada {cont} ) :  ')))
                        print()
                        jogador2_pontos.append(int(input(f'\n Digite a nota de ( {jogador2_nome} rodada {cont}) :   ')))
                        
                            # print()
                            
                            
                # tratamento de erros        
                except (Exception,ValueError):
                    print('\033[0;31mPorfavor digite apenas numeros inteiros para os pontos dos competidores que seja acima de zero e menor que dez! \n \033[m')
                    maybe = False
                
                for cont in range(0,5):
                    if jogador1_pontos[cont] < 0:
                        maybe = False
                    if jogador2_pontos[cont] < 0:
                        maybe = False
                    if maybe == False:
                        break
                
                for cont in range(0,5):
                    if jogador1_pontos[cont] > 10:
                        maybe = False
                    if jogador2_pontos[cont] > 10:
                        maybe = False
                    if maybe == False:
                        break          
                        
                if maybe == False:
                    print('\033[0;31mPorfavor digite apenas numeros inteiros para os pontos dos competidores que seja acima de zero e menor que dez! \n \033[m')
                    jogador1_pontos = []
                    jogador2_pontos = []
                
                
                if maybe == True:
                    if len(jogador1_pontos) == 5 and len(jogador2_pontos) == 5:
                        break
            
                
            print()
            print()
            
            # Printando os pontos obtidos dos dois competidores
            for c,i in enumerate(jogador1_pontos):
                c += 1
                print(f'Jogador *** {jogador1_nome} *** rodada {c} arremesso : {i}   ')
                # print(i)
            
            print()
            print()    
            
            for c,i in enumerate(jogador2_pontos):
                c += 1
                print(f'Jogador *** {jogador2_nome} ***  rodada {c} arremesso : {i}   ')
                # print(i)
            
            print()    
            print()
            
            # Ordenando vetores com pontos dos competidores
            for cont  in range(0,5):
                
                jogador1_pontos.sort()
            
            for cont  in range(0,5):
                
                jogador2_pontos.sort()
            
            print()
            print()
                
            # Remove a primeira casa com o menor valor
            jogador1_pontos.pop(0)
            jogador2_pontos.pop(0)
            

            # Soma o valor dos dois competidores e em seguida determina qual foi o maior valor ( VENCEDOR ) 
            jogador1_pontoss = sum(jogador1_pontos)
            jogador2_pontoss = sum(jogador2_pontos)
            
            
            print('\033[0;32mPARABENS! \n \033[m')          
            # valida o vencedor
            if(jogador1_pontoss > jogador2_pontoss):
                print(f'\033[0;32mCompetidor {jogador1_nome} venceu a olimpiada por {jogador1_pontoss} pontos! \n \033[m')
            else:
                print(f'\033[0;32mCompetidor {jogador2_nome} venceu a olimpiada por {jogador2_pontoss} pontos! \n \033[m')
            
            
            print('*'*100)
            print(''*50+ 'Fim das Olimpiadas ')
            print('*'*100)
            print()
            print()
            print()
            


