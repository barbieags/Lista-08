Implemente uma classe Empregado com os seguintes atributos: nome, idade e salario. Crie os métodos promover(), aumentarSalario(), demitir() e fazerAniversario().

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
