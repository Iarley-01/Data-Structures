# Data-Structures
Programs using Data Structures in C
# Name: Iarley Alves da Silva
# Description: Vector Operations

#include <stdlib.h>
#include <stdio.h>
#include <time.h>
#include <locale.h>
#include <stdbool.h>

int maiorNum(int vetor[], int t){
	int i=0;
	int m;
	
	m=vetor[i];
	for (i=0; i<t; i++){
		if (m<vetor[i]){
			m=vetor[i];
		}
	}
	
	return m;
}

int numPar(int vetor[], int t){
	int i;
	int p=0;
	
	for (i=0; i<t; i++){
		if (vetor[i]%2==0){
			p++;
		}
	}
	return p;
}

int soma(int vetor[], int t){
	int i;
	int soma=0;
	
	for (i=0; i<t; i++){
		soma=soma+vetor[i];
	}
	return soma;
}

void inverter(int vetor[], int ini, int f){
	int aux;
	if (ini<f){
		aux=vetor[ini];
		vetor[ini]=vetor[f];
		vetor[f]=aux;
		inverter(vetor, ini+1, f-1);
	}
}

void mostrar(int vetor[], int t){
	if(t==1){
		printf("%d - ", vetor[t-1]);
	}
	else{
		mostrar(vetor, t-1);
		printf("%d - ", vetor[t-1]);
	}
}

int main(){
	int op=0;
	int vet[10], S, maior, pares;
	bool vetor=false;
	setlocale(LC_ALL, "Portuguese");
	srand(time(NULL));		
	
	while(op!= 6){
    printf("\n\n=============MENU==========\n\nEscolha uma Opção:");
		printf("\n[1] Gerar vetor de 10 números aleatórios\n[2] Ver o maior número do vetor\n[3] Ver a quantidade de números pares\n[4] Ver o resultado da soma dos elementos do vetor\n[5] Inverter o vetor\n[6] Sair\n\nOpção: ");
		scanf("%d", &op);
	
		switch(op){
			case 1:
			vetor=true;
        printf("\n\nVetor Gerado: ");
				for (int i=0; i<10; i++)
					vet[i]=rand()%100;
					printf("\n\n");
				for (int i=0; i<10; i++)
					printf("%d - ", vet[i]);
					printf("\n\n");
			break;
			case 2:
			if(vetor==true){
				maior=maiorNum(vet, 10);
				printf("\nMaior Número: %d", maior);
			}
			else {
			    printf("\n\nO vetor não foi gerado\nAção Inválida");
			}
			break;
			case 3:
			if(vetor==true){
				pares=numPar(vet, 10);
				printf("\nQuantidade de Números Pares: %d", pares); 
			}
			else {
			    printf("\n\nO vetor não foi gerado\nAção Inválida");
			}
			break;
			case 4:
			if(vetor==true){
				S=soma(vet, 10);
				printf("\nSoma dos números do vetor: %d", S);
			}
			else {
			    printf("\n\nO vetor não foi gerado\nAção Inválida");
			}
			break;
			case 5:
			if(vetor==true){
        printf("\n\nVetor Normal: \n");
				mostrar(vet, 10);
				inverter(vet, 0, 9);
				printf("\n\n");
        printf("\n\nVetor Invertido: \n");
				mostrar(vet, 10);
			}
			else {
			    printf("\n\nO vetor não foi gerado\nAção Inválida");
			}
			break;
			case 6:
				printf("Saindo...");
			break;
			default:
				printf("\nOpção Inválida");
			break;
		}
	}
	return 0;
}
