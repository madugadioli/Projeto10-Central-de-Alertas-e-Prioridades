#include <iostream>
using namespace std;

int main() {

    int eventos[4][5];
    int peso[4] = {1, 2, 3, 4};
    int totais[4] = {0, 0, 0, 0};
    int pontos[4] = {0, 0, 0, 0};

    int maiorPontuacao = 0;
    int maiorCategoria = 0;

    cout << " CENTRAL DE ALERTAS E PRIORIDADES" << endl;

    cout << "\nCategorias:" << endl;
    cout << "1 - Phishing" << endl;
    cout << "2 - Falhas de login" << endl;
    cout << "3 - Malware" << endl;
    cout << "4 - Configuracoes expostas" << endl;
    cout << "\nDigite a quantidade de eventos de cada categoria." << endl;
    cout << "Os valores devem estar entre 0 e 20.\n" << endl;
    
    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 5; j++) {
            cout << "Categoria " << i + 1;
            cout << " - Dia " << j + 1 << ": ";
            cin >> eventos[i][j];
            while (eventos[i][j] < 0 || eventos[i][j] > 20) {
                cout << "Valor invalido! Digite entre 0 e 20: ";
                cin >> eventos[i][j];
            }
        }
    }

    for (int i = 0; i < 4; i++) {
        for (int j = 0; j < 5; j++) {
            totais[i] = totais[i] + eventos[i][j];
        }
        pontos[i] = totais[i] * peso[i];
    }

    maiorPontuacao = pontos[0];
    maiorCategoria = 0;
    for (int i = 1; i < 4; i++) {
        if (pontos[i] > maiorPontuacao) {
            maiorPontuacao = pontos[i];
            maiorCategoria = i;
        }
    }

    cout << "          PAINEL DE SEGURANCA" << endl;
    for (int i = 0; i < 4; i++) {
        cout << "\nCategoria: ";
        if (i == 0) {
            cout << "Phishing";
        }
        else if (i == 1) {
            cout << "Falhas de login";
        }
        else if (i == 2) {
            cout << "Malware";
        }
        else {
            cout << "Configuracoes expostas";
        }
        cout << "\nTotal de eventos: " << totais[i];
        cout << "\nPeso: " << peso[i];
        cout << "\nPontuacao: " << pontos[i];
        if (pontos[i] >= 10) {
            cout << "\nPRIORIDADE ALTA!";
        }
        else {
            cout << "\nSem prioridade alta.";
        }
        cout << "\n------------------------------------" << endl;
    }
    
    cout << "\nCATEGORIA COM MAIOR PONTUACAO: ";
    if (maiorCategoria == 0) {
        cout << "Phishing";
    }
    else if (maiorCategoria == 1) {
        cout << "Falhas de login";
    }
    else if (maiorCategoria == 2) {
        cout << "Malware";
    }
    else {
        cout << "Configuracoes expostas";
    }
    cout << "\nMaior pontuacao: " << maiorPontuacao << endl;
    cout << "          FIM DA ANALISE" << endl;
    return 0;
}
