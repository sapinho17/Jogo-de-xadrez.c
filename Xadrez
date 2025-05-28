#include <stdio.h>

#define SIZE 8

// Mostra o tabuleiro com os movimentos possíveis
void mostrarTabuleiro(int tabuleiro[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        for (int j = 0; j < SIZE; j++) {
            printf("%d ", tabuleiro[i][j]);
        }
        printf("\n");
    }
}

// Zera o tabuleiro
void limparTabuleiro(int tabuleiro[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; i++)
        for (int j = 0; j < SIZE; j++)
            tabuleiro[i][j] = 0;
}

// Torre: movimentos em linha reta (repetição simples)
void moverTorre(int x, int y, int tabuleiro[SIZE][SIZE]) {
    for (int i = 0; i < SIZE; i++) {
        tabuleiro[x][i] = 1;  // horizontal
        tabuleiro[i][y] = 1;  // vertical
    }
    tabuleiro[x][y] = 8;  // posição da peça
}

// Bispo: movimentos em diagonal (repetição simples)
void moverBispo(int x, int y, int tabuleiro[SIZE][SIZE]) {
    for (int i = -SIZE; i < SIZE; i++) {
        if (x + i >= 0 && x + i < SIZE && y + i >= 0 && y + i < SIZE)
            tabuleiro[x + i][y + i] = 1;
        if (x + i >= 0 && x + i < SIZE && y - i >= 0 && y - i < SIZE)
            tabuleiro[x + i][y - i] = 1;
    }
    tabuleiro[x][y] = 8;
}

// Rainha: combinação de torre e bispo (repetição simples)
void moverRainha(int x, int y, int tabuleiro[SIZE][SIZE]) {
    moverTorre(x, y, tabuleiro);
    moverBispo(x, y, tabuleiro);
}

// Cavalo: movimento em L (loops aninhados)
void moverCavalo(int x, int y, int tabuleiro[SIZE][SIZE]) {
    int dx[] = { 2, 1, -1, -2, -2, -1, 1, 2 };
    int dy[] = { 1, 2, 2, 1, -1, -2, -2, -1 };
    
    for (int i = 0; i < 8; i++) {
        int nx = x + dx[i];
        int ny = y + dy[i];
        if (nx >= 0 && nx < SIZE && ny >= 0 && ny < SIZE)
            tabuleiro[nx][ny] = 1;
    }
    tabuleiro[x][y] = 8;
}

// Rainha Avançada: usando recursividade
void marcarRainhaRecursiva(int x, int y, int dx, int dy, int tabuleiro[SIZE][SIZE]) {
    int nx = x + dx;
    int ny = y + dy;
    if (nx >= 0 && nx < SIZE && ny >= 0 && ny < SIZE) {
        tabuleiro[nx][ny] = 1;
        marcarRainhaRecursiva(nx, ny, dx, dy, tabuleiro);
    }
}

void moverRainhaAvancada(int x, int y, int tabuleiro[SIZE][SIZE]) {
    int dirs[8][2] = { {1,0}, {-1,0}, {0,1}, {0,-1}, {1,1}, {-1,-1}, {1,-1}, {-1,1} };
    for (int i = 0; i < 8; i++) {
        marcarRainhaRecursiva(x, y, dirs[i][0], dirs[i][1], tabuleiro);
    }
    tabuleiro[x][y] = 8;
}

int main() {
    int tabuleiro[SIZE][SIZE];
    int x = 3, y = 3;

    printf("Movimentos da Torre:\n");
    limparTabuleiro(tabuleiro);
    moverTorre(x, y, tabuleiro);
    mostrarTabuleiro(tabuleiro);

    printf("\nMovimentos do Bispo:\n");
    limparTabuleiro(tabuleiro);
    moverBispo(x, y, tabuleiro);
    mostrarTabuleiro(tabuleiro);

    printf("\nMovimentos da Rainha:\n");
    limparTabuleiro(tabuleiro);
    moverRainha(x, y, tabuleiro);
    mostrarTabuleiro(tabuleiro);

    printf("\nMovimentos do Cavalo:\n");
    limparTabuleiro(tabuleiro);
    moverCavalo(x, y, tabuleiro);
    mostrarTabuleiro(tabuleiro);

    printf("\nMovimentos da Rainha (Recursiva):\n");
    limparTabuleiro(tabuleiro);
    moverRainhaAvancada(x, y, tabuleiro);
    mostrarTabuleiro(tabuleiro);

    return 0;
}
