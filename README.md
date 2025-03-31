# jogos-girotto
## trabalho
o programa foi desenvolvido por (André Almeida e Alexandre Arthur)
com o uso de IA para consulta somente, foram usados: Chatgpt e DeepSeek
aqui está o código:

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define MAX_GOUSMAS 2
#define FURIA_MAX 5
#define FURIA_INICIAL 1

typedef struct Gousma {
    int furia;
} Gousma;

void inicializar_jogador(Gousma gousmas[MAX_GOUSMAS]) {
    for (int i = 0; i < MAX_GOUSMAS; i++) {
        gousmas[i].furia = FURIA_INICIAL; 
    }
}

void exibir_gousmas(Gousma gousmas[MAX_GOUSMAS]) {
    for (int i = 0; i < MAX_GOUSMAS; i++) {
        if (gousmas[i].furia > 0) {
            printf("Gousma %d: Furia = %d\n", i + 1, gousmas[i].furia);
        }
    }
}

void atacar(Gousma *atacante, Gousma *defensor) {
    defensor->furia += atacante->furia;
    atacante->furia = 0;
    if (defensor->furia > FURIA_MAX) {
        defensor->furia = 0; 
        printf("A Gousma se desintegrou devido a furia excessiva!\n");
    }
}

int verificar_derrota(Gousma gousmas[MAX_GOUSMAS]) {
    for (int i = 0; i < MAX_GOUSMAS; i++) {
        if (gousmas[i].furia > 0) {
            return 0; 
        }
    }
    return 1; 
}

void jogar_gousmas() {
    Gousma jogador1[MAX_GOUSMAS], jogador2[MAX_GOUSMAS];
    int turno = 1;
    int opcao, gousma_atacante, gousma_defensora;
    
    inicializar_jogador(jogador1);
    inicializar_jogador(jogador2);

    while (1) {
        printf("\nTurno do Jogador %d\n", turno);
        if (turno == 1) {
            printf("Gousmas do Jogador 1:\n");
            exibir_gousmas(jogador1);
        } else {
            printf("Gousmas do Jogador 2:\n");
            exibir_gousmas(jogador2);
        }

        printf("Escolha uma opcao:\n");
        printf("1. Atacar\n");
        printf("2. Finalizar turno\n");
        printf("Escolha: ");
        scanf("%d", &opcao);

        if (opcao == 1) {
            printf("Escolha a Gousma atacante (1 ou 2): ");
            scanf("%d", &gousma_atacante);
            gousma_atacante--; 

            printf("Escolha a Gousma pra atacar (1 ou 2): ");
            scanf("%d", &gousma_defensora);
            gousma_defensora--;

            if (turno == 1 && jogador1[gousma_atacante].furia > 0 && jogador2[gousma_defensora].furia > 0) {
                atacar(&jogador1[gousma_atacante], &jogador2[gousma_defensora]);
            } else if (turno == 2 && jogador2[gousma_atacante].furia > 0 && jogador1[gousma_defensora].furia > 0) {
                atacar(&jogador2[gousma_atacante], &jogador1[gousma_defensora]);
            } else {
                printf("Escolha invalida ou Gousma sem fúria!\n");
                continue;
            }
        }

        
        if (verificar_derrota(jogador1)) {
            printf("Jogador 2 venceu!\n");
            break;
        } else if (verificar_derrota(jogador2)) {
            printf("Jogador 1 venceu!\n");
            break;
        }

        turno = (turno == 1) ? 2 : 1;
    }
}

int sort_jogador() {
    int primeiro_jogador = rand() % 7;
    primeiro_jogador;
}
int main() {
    int x;
    char c, s, z;
    srand(time(NULL));
    while (1) {
        printf("|=======MINI GAMES=======|\n|1:Perguntas e Respostas |\n|2:Cobra na Caixa!       |\n|3:Gousmas War           |\n|4:Sair                  |\n|========================|\n");
        scanf("%d", &x);
        getchar();

        if (x == 1) {
            while (1) {
                printf("Voce escolheu: Perguntas e respostas!\n\n");
                
                printf("1. Quem descobriu o Brasil?\n\n");
                printf("a) Pedro Alvares Cabral\n");
                printf("b) Cristovao Colombo\n");
                printf("c) Mick Jagger\n\n");
                printf("Resposta: ");
                scanf(" %c", &c);
                getchar();
                if (c == 'a') {
                    printf("\nParabens! Acertou!\n\n");
                } else {
                    printf("\nErrado! Tente novamente\n\n");
                }

                printf("2. Quanto e 1+1?\n\n");
                printf("a) 2\n");
                printf("b) 3\n");
                printf("c) 4\n\n");
                printf("Resposta: ");
                scanf(" %c", &s);
                getchar();
                if (s == 'a') {
                    printf("\nParabens! Voce acertou!\n\n");
                } else {
                    printf("\nErrado! Tente Novamente!\n\n");
                }

                printf("3. Quem vendeu o Alasca para os Estados Unidos?\n\n");
                printf("a) Canada\n");
                printf("b) Russia\n");
                printf("c) Imperio Bizantino\n\n");
                printf("Resposta: ");
                scanf("%c", &z);
                getchar();
                if (z == 'b') {
                    printf("\nParabens! Acertou!\n\n");
                } else {
                    printf("\nErrado! Tente Novamente!\n\n");
                }
                
                char opcao;
                printf("\nDeseja jogar novamente? (s/n): ");
                scanf("%c", &opcao);
                getchar();
                if (opcao == 'n') break;
            }
        }
        else if(x == 2) {
    char opcao2;
    char* jogadores[] = {"Alexandre", "Andre", "João", "Athos", "Josiel", "Caio", "Arthur"};
    
    do {
        int jogador1 = rand() % 7;
        int jogador2;
        do {
            jogador2 = rand() % 7;
        } while(jogador2 == jogador1);
        
        printf("\nOs exploradores desta aventura sao: %s e %s!\n", 
               jogadores[jogador1], jogadores[jogador2]);
        
        int primeiro_jogador = rand() % 2;
        printf("%s vai comecar a exploracao!\n", 
               primeiro_jogador == 0 ? jogadores[jogador1] : jogadores[jogador2]);
        
        int botao_pos = rand() % 5 + 1;
        int cobra_pos;
        do {
            cobra_pos = rand() % 5 + 1;
        } while(cobra_pos == botao_pos);
        
        int resultado = 0;
        while(resultado == 0) {
            int y;
            printf("\n%s, faca sua escolha:\n", 
                   primeiro_jogador == 0 ? jogadores[jogador1] : jogadores[jogador2]);
            printf("\n\nCaixa 1\n\nCaixa 2\n\nCaixa 3\n\nCaixa 4\n\nCaixa 5\n\n");
            printf("faca sua escolha: ");
            
            if(scanf("%d", &y) != 1) {
                printf("Isso nao e uma escolha valida!\n");
                while(getchar() != '\n');
                continue;
            }
            
            if(y < 1 || y > 5) {
                printf("Escolha deve ser entre 1 e 5!\n");
                continue;
            }
            
            if(y == cobra_pos) {
                printf("\n voce achou a cobra e morreu :(\n",
                       primeiro_jogador == 0 ? jogadores[jogador1] : jogadores[jogador2],
                       y,
                       primeiro_jogador == 0 ? jogadores[jogador1] : jogadores[jogador2]);
                resultado = -1;
            }
            else if(y == botao_pos) {
                printf("\n%s voce achou o botao parabens! :)\n",
                       primeiro_jogador == 0 ? jogadores[jogador1] : jogadores[jogador2],
                       y,
                       jogadores[jogador1], jogadores[jogador2]);
                resultado = 1;
            }
            else {
                printf("nada aqui, tente de novo\n", y);
                primeiro_jogador = (primeiro_jogador + 1) % 2;
                printf("Agora e a vez de %s!\n", 
                       primeiro_jogador == 0 ? jogadores[jogador1] : jogadores[jogador2]);
            }
        }
        
        printf("\n quer jogar novamente? (s/n): ");
        scanf(" %c", &opcao2);
        getchar();
        
    } while(opcao2 == 's' || opcao2 == 'S');
}
		else if (x==3){
			jogar_gousmas();
			char opcao2;
			printf("deseja jogar novamente(s/n)");
			scanf("%c",&opcao2);
			getchar();
			if (opcao2=='n')break;
		}
		      
		else if (x == 4) {
            printf("ate mais\n");
            break;
        }
    }
    return 0;
}
