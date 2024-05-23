Implemente uma classe Empregado com os seguintes atributos: nome, idade e salario. Crie os métodos promover(), aumentarSalario(), demitir() e fazerAniversario().

package com.mycompany.lista8;
public class Empregado {

    private String nome;
    private int idade;
    private double salario;

    // Atributos publicos
    public Empregado(String nome, int idade, double salario) {
        //acho que vai ser o int porque idade é preciso, numero inteiro) (salário é double porque posso colocar muitas casas decimais)
        //uso o this quando a variavél estiver com o mesmo nome do metódo
        this.nome = nome;
        this.idade = idade;
        this.salario = salario;
    }

    // Get e set para todos os atributos
    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public int getIdade() {
        return idade;
    }

    public void setIdade(int idade) {
        this.idade = idade;
    }

    public double getSalario() {
        return salario;
    }

    public void setSalario(double salario) {
        this.salario = salario;
    }

    public String toString() {
        return "Empregado{"
                + "nome='" + nome + '\''
                + ", idade=" + idade
                + ", salario=" + salario
                + '}';
    }

    // Método para promover o empregado 
    public void promover() {
        if (idade > 18) {
            double aumento = salario * 0.25; // 25% de aumento
            aumentarSalario(aumento);
        } else {
            System.out.println(nome + " O empregado deve ter mais de 18 anos para ser promovido.");
        }
    }

    // Método para aumentar o salário de acordo com o porcentual informado
    public void aumentarSalario(double porcentual) {
        salario += salario * (porcentual / 100);
        System.out.println("Valor do salário após o aumento: " + salario);
    }

    // Método para demitir o empregado
    public void demitir(int motivo) {
        switch (motivo) {
            case 1: // Justa causa
                System.out.println("Demitido por justa causa. Deve cumprir aviso prévio.");
                break;
            case 2: // Decisão do empregador
                double multa = salario * 0.4;
                salario -= multa;
                System.out.println("Demitido por decisão do empregador. Multa aplicada: " + multa);
                break;
            case 3: // Aposentadoria
                double salarioAposentadoria;
                if (salario >= 1000 && salario < 2000) {
                    salarioAposentadoria = 1500;
                } else if (salario >= 2000 && salario < 3000) {
                    salarioAposentadoria = 2500;
                } else if (salario >= 3000 && salario < 4000) {
                    salarioAposentadoria = 3500;
                } else {
                    salarioAposentadoria = 4000;
                }
                salario = salarioAposentadoria;
                System.out.println("Valor do Salário de aposentadoria: " + salario);
                break;
        }
    }

    // Método para fazer aniversário (aumenta a idade do empregado em 1 ano)
    public void fazerAniversario() {
        idade++;
        System.out.println("Feliz aniversário! Nova idade: " + idade);
    }
}


Crie uma classe Principal com um menu interativo para testar a classe Empregado. O menu deve permitir ao usuário escolher as seguintes opções para manipular uma lista de empregados:
- Criar novo empregado
- Promover empregado
- Aumentar salário do empregado
- Demitir empregado
- Fazer aniversário do empregado
- Mostrar detalhes dos empregados
- Sair

package com.mycompany.lista8;

import java.util.ArrayList;
import java.util.Scanner;

public class Lista8 {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Empregado> empregados = new ArrayList<>();

        int opcao;
        do {
            System.out.println("\nMenu:");
            System.out.println("1. Criar novo empregado");
            System.out.println("2. Promover empregado");
            System.out.println("3. Aumentar salário do empregado");
            System.out.println("4. Demitir empregado");
            System.out.println("5. Fazer aniversário do empregado");
            System.out.println("6. Mostrar detalhes dos empregados");
            System.out.println("7. Sair");
            System.out.print("Escolha uma opção: ");
            opcao = scanner.nextInt();

            switch (opcao) {
                case 1:
                    criarEmpregado(empregados, scanner);
                    break;
                case 2:
                    promoverEmpregado(empregados, scanner);
                    break;
                case 3:
                    aumentarSalarioEmpregado(empregados, scanner);
                    break;
                case 4:
                    demitirEmpregado(empregados, scanner);
                    break;
                case 5:
                    fazerAniversarioEmpregado(empregados, scanner);
                    break;
                case 6:
                    mostrarDetalhesEmpregados(empregados);
                    break;
                case 7:
                    System.out.println("Saindo...");
                    break;
                default:
                    System.out.println("Opção inválida.");
            }
        } while (opcao != 7);
    }

    public static void criarEmpregado(ArrayList<Empregado> empregados, Scanner scanner) {
        System.out.print("Nome do empregado: ");
        String nome = scanner.next();
        System.out.print("Idade do empregado: ");
        int idade = scanner.nextInt();
        System.out.print("Salário do empregado: ");
        double salario = scanner.nextDouble();
        empregados.add(new Empregado(nome, idade, salario));
        System.out.println("Empregado criado com sucesso.");
    }

    public static void promoverEmpregado(ArrayList<Empregado> empregados, Scanner scanner) {
        System.out.print("Índice do empregado a ser promovido: ");
        int indice = scanner.nextInt();
        if (indice >= 0 && indice < empregados.size()) {
            empregados.get(indice).promover();
        } else {
            System.out.println("Índice inválido.");
        }
    }

    public static void aumentarSalarioEmpregado(ArrayList<Empregado> empregados, Scanner scanner) {
        System.out.print("Índice do empregado a ter o salário aumentado: ");
        int indice = scanner.nextInt();
        if (indice >= 0 && indice < empregados.size()) {
            System.out.print("Percentual de aumento do salário: ");
            double percentual = scanner.nextDouble();
            empregados.get(indice).aumentarSalario(percentual);
        } else {
            System.out.println("Índice inválido.");
        }
    }

    public static void demitirEmpregado(ArrayList<Empregado> empregados, Scanner scanner) {
        System.out.print("Índice do empregado a ser demitido: ");
        int indice = scanner.nextInt();
        if (indice >= 0 && indice < empregados.size()) {
            System.out.println("Escolha o motivo da demissão:");
            System.out.println("1. Justa causa");
            System.out.println("2. Decisão do empregador");
            System.out.println("3. Aposentadoria");
            int motivo = scanner.nextInt();
            empregados.get(indice).demitir(motivo);
            empregados.remove(indice); // Remove o empregado da lista após a demissão
        } else {
            System.out.println("Índice inválido.");
        }
    }

    private static void fazerAniversarioEmpregado(ArrayList<Empregado> empregados, Scanner scanner) {
        System.out.print("Índice do empregado: ");
        int indice = scanner.nextInt();
        if (indice >= 0 && indice < empregados.size()) {
            Empregado empregado = empregados.get(indice);
            empregado.fazerAniversario();
        } else {
            System.out.println("Índice inválido.");
        }
    }

    private static void mostrarDetalhesEmpregados(ArrayList<Empregado> empregados) {
        System.out.println("Detalhes dos Empregados:");
        for (int i = 0; i < empregados.size(); i++) {
            System.out.println("Empregado " + (i+1) + ": " + empregados.get(i));
        }
    }
}



