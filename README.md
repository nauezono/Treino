#include <stdio.h>
#include <string.h>

// --- Definições de Constantes ---
#define MAX_TERRITORIOS 5
#define TAM_NOME 30
#define TAM_COR 10

// --- Criação da Struct ---
// Representa o molde para cada território no jogo.
struct Territorio {
    char nome[TAM_NOME];
    char cor[TAM_COR];
    int tropas;
};

// Função para limpar o rastro do "Enter" no teclado
void limparBuffer() {
    int c;
    while ((c = getchar()) != '\n' && c != EOF);
}

int main() {
    // Declaração do vetor de structs (capacidade para 5 territórios)
    struct Territorio mapa[MAX_TERRITORIOS];
    int i;

    printf("==========================================\n");
    printf("     CADASTRO DE TERRITORIOS DE GUERRA\n");
    printf("==========================================\n\n");

    // --- ENTRADA DOS DADOS ---
    // Este laço se repetirá exatamente 5 vezes (de 0 a 4)
    for (i = 0; i < MAX_TERRITORIOS; i++) {
        printf("Territorio #%d\n", i + 1);

        printf("Nome do Territorio: ");
        // Usamos scanf com %[^\n] para ler espaços se o nome for composto (ex: Brazil Central)
        scanf(" %[^\n]s", mapa[i].nome);
        limparBuffer();

        printf("Cor do Exercito: ");
        scanf(" %s", mapa[i].cor);
        limparBuffer();

        printf("Quantidade de Tropas: ");
        scanf("%d", &mapa[i].tropas);
        limparBuffer();

        printf("------------------------------------------\n");
    }

    // --- EXIBIÇÃO DOS DADOS ---
    // O sistema apresenta os dados logo após o cadastro
    printf("\n\nRELATORIO FINAL DE TERRITORIOS:\n");
    printf("==========================================\n");

    for (i = 0; i < MAX_TERRITORIOS; i++) {
        printf("TERRITORIO: %-15s | COR: %-10s | TROPAS: %d\n", 
                mapa[i].nome, mapa[i].cor, mapa[i].tropas);
    }

    printf("==========================================\n");
    printf("Fim do programa.\n");

    return 0;
}
