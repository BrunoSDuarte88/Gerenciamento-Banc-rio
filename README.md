# Gerenciamento Bancario - java
Aula Prática - Linguagem Orientada a Objetos

/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 */

package com.mycompany.gerenciabanco;

import java.util.Scanner;

/**
 *
 * @author sdbru
 * 
 */

class Cliente {

    private String nome;
    private String sobrenome;
    private String cpf;
    private double saldo;
    
    public Cliente (String nome, String sobrenome, String cpf) {
        this.nome = nome;
        this.sobrenome = sobrenome;
        this.cpf = cpf;
        this.saldo = 0.0;
    }
    
    
    public void consultarSaldo() {
        System.out.println("Saldo atual é R$" + saldo);
    }
    
    public void depositar(double valor) {
        if (valor > 0) {
            saldo += valor;
            System.out.println("Deposito de R$" + valor + "realizado com sucesso.");
        }else {
            System.out.println("Valor de deposito invalido!");
        }
    }
    
    public void sacar(double valor) {
        if (valor > 0 && valor <= saldo) {
            saldo -= valor;
            System.out.println("Saque de R$" + valor + "realizado com sucesso.");
        }else {
            System.out.println("Saldo insuficiente ou valor de saque invalido.");
        }
    }
}




public class GerenciaBanco{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Informe seu nome:");
        String nome = scanner.nextLine();
        System.out.println("Informe seu sobrenome:");
        String sobrenome = scanner.nextLine();
        System.out.println("Informe seu CPF:");
        String cpf = scanner.nextLine();
        
        Cliente cliente = new Cliente(nome, sobrenome, cpf);
        
        boolean continuar = true;
        while(continuar) {
            System.out.println("\n O que deseja?");
            System.out.println("1 - Consultar saldo");
            System.out.println("2 - Realizar deposito");
            System.out.println("3 - Realizar saque");
            System.out.println("4 - Sair\n\n");
            
            int escolha = scanner.nextInt();
            switch (escolha) {
                case 1:
                    cliente.consultarSaldo();
                    break;
                case 2:
                    System.out.println("Informe o valor a ser depositado:");
                    double valorDeposito = scanner.nextDouble();
                    cliente.depositar(valorDeposito);
                    break;
                case 3:
                    System.out.println("Informe o valor de saque:");
                    double valorSaque = scanner.nextDouble();
                    cliente.sacar(valorSaque);
                    break;
                case 4: 
                    continuar = false;
                    System.out.println("Encerrando a aplicação.");
                    break;
                default:
                    System.out.println("Opção invalida, tente novamente.");
                    break;
            }
        }
        scanner.close();
    }
}
