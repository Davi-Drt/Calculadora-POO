# Calculadora-POO

#include <iostream>
using namespace std;

// Classe base
class Calculadora {
public:
    // Métodos virtuais (para sobrescrita)
    virtual double calcular(double a, double b) {
        return 0;
    }
};

// Classes derivadas (sobrescrita)
class Soma : public Calculadora {
public:
    double calcular(double a, double b) override {
        return a + b;
    }
};

class Subtracao : public Calculadora {
public:
    double calcular(double a, double b) override {
        return a - b;
    }
};

class Multiplicacao : public Calculadora {
public:
    double calcular(double a, double b) override {
        return a * b;
    }
};

class Divisao : public Calculadora {
public:
    double calcular(double a, double b) override {
        if (b == 0) {
            cout << "Erro: divisão por zero!" << endl;
            return 0;
        }
        return a / b;
    }
};

// Classe com SOBRECARGA
class CalculadoraOverload {
public:
    int soma(int a, int b) {
        return a + b;
    }

    double soma(double a, double b) {
        return a + b;
    }

    double soma(double a, double b, double c) {
        return a + b + c;
    }
};

int main() {
    double a, b;
    int opcao;

    cout << "Digite dois números: ";
    cin >> a >> b;

    cout << "\nEscolha a operação:\n";
    cout << "1 - Soma\n";
    cout << "2 - Subtração\n";
    cout << "3 - Multiplicação\n";
    cout << "4 - Divisão\n";
    cin >> opcao;

    Calculadora* calc;

    switch (opcao) {
        case 1:
            calc = new Soma();
            break;
        case 2:
            calc = new Subtracao();
            break;
        case 3:
            calc = new Multiplicacao();
            break;
        case 4:
            calc = new Divisao();
            break;
        default:
            cout << "Opção inválida!" << endl;
            return 0;
    }

    cout << "Resultado: " << calc->calcular(a, b) << endl;

    delete calc;

    // Teste da SOBRECARGA
    CalculadoraOverload c;
    cout << "\nTestando sobrecarga:" << endl;
    cout << "Soma int: " << c.soma(2, 3) << endl;
    cout << "Soma double: " << c.soma(2.5, 3.5) << endl;
    cout << "Soma 3 valores: " << c.soma(1.1, 2.2, 3.3) << endl;
    
    return 0;
}
