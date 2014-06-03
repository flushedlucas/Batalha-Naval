Batalha-Naval
=============

Projeto de Introdução a Programação 
Turma SI 2 
Lucas Filipe e Eridson Igor.md



	from random import *
	
	secura = 'S'
	
	while secura == 'S':
	
		while True:
		    linhas = input('Digite o numero de linhas: ')
		    if linhas < 3:
		        print 'O numero mínimo de linhas é 3'
		    else:
		        break
		
		while True:
		    colunas = input('Digite o numero de colunas: ')
		    if colunas < 3:
		        print 'O numero minimo de colunas é 3'
		    else:
		        break
		
		while True: 
		    navios = input('Digite o numero de navios: ')
		    if navios > (linhas*colunas):
		        print 'O numero de navios deve ser menor que a quantidade de posições no grid'
		    else:
		        break
		while True:
		    erros = input('Digite a quantidade de erros permitidos: ')
		    if erros < navios and erros > (linhas*colunas):
		        print " O numero de erros deve ser maior que o numero de navios e menor que o tamanho do grid"
		    else:
		        break
	
	mat1 = ['.']*linhas
	for i in range(linhas):
	    mat1[i] = ['.']*colunas
	ex = ['.']*linhas
	for i in range(linhas):
	    ex[i] = ['.']*colunas
	
	for i in range(len(ex)):
	    print ex[i]
	
	pos = 0
	while pos < navios:
	    x = randint(0, colunas-1)
	    y = randint(0, linhas-1)
	    if mat1[y][x] == 'N':
	        continue
	    else:
	        mat1[y][x] = 'N'
	        pos +=1
	tentativas = 0
	acertos = 0
	while tentativas <= erros:
	    coordenadas = True
	    print 'Digite a coordenada especificando a linha e a coluna(L,C)'
	    while True:
	        coo_linha = input('Linha: ')
	        if coo_linha > (linhas):
	            print 'Linha inexistente'
	        else:
	            break
	    while True:
	        coo_coluna = input('Coluna: ')
	        if coo_coluna > (colunas):
	            print 'Coluna inexistente'
	        else:
	            break
	    while coordenadas == True:
	        if  ex[coo_linha - 1][coo_coluna - 1] != '.':
	            coordenadas = False
	            print ('Coordenada ja utilizada')
	        else:
	            break
	    if coordenadas == True:
	        while True:
	            if mat1[coo_linha - 1][coo_coluna - 1]== 'N':
	                ex[coo_linha - 1][coo_coluna - 1] = 'X'
	                for i, p in enumerate(ex):
	                    print i + 1, ' ', p
	                print 'Voce acertou um navio'
	                acertos += 1
	                break
	            elif mat1[coo_linha - 1][coo_coluna - 1]== '.':
	                ex[coo_linha - 1][coo_coluna - 1] = '0'
	                for i, p in enumerate(ex):
	                        print i + 1, ' ', p
	                print'Voce não acertou nenhum alvo'
	                tentativas += 1
	                break
	        if acertos == navios:
	             print 'Parabens voce acertou todos os navios'
	             break
	        elif tentativas > erros:
	             print 'Que pena, voce perdeu!'
	    else:
	        coordenadas = False
	secura = raw_input ("Deseja jogar novamente? (S/N): ")
	secura.upper()
