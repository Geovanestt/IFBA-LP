/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Main.java to edit this template
 */
package class_exercise.pkg1;

/**
 *
 * @author Geovane
 */  
import java.time.LocalDate;
import java.time.temporal.ChronoUnit;
import java.util.Scanner;

class Funcionario{
    private String nome;
    private LocalDate dataAdmissao; // Data de admissão
    private double valorHora;
    private float horasTrabalhadas;

    public Funcionario(String nome, String dataAdmissao, double valorHora, float horasTrabalhadas) {
        this.nome = nome;
        this.dataAdmissao = LocalDate.parse(dataAdmissao); // Convertendo string para LocalDate
        this.valorHora = valorHora;
        this.horasTrabalhadas = horasTrabalhadas;
    }

    public int calcularTempoEmpresa() {
        LocalDate hoje = LocalDate.now();
        return (int) ChronoUnit.YEARS.between(dataAdmissao, hoje); // Calculando anos
    }

    public double calcularSalario() {
        int anosEmpresa = calcularTempoEmpresa();
        double salarioBase = valorHora * horasTrabalhadas;
        double aumento = 0;

        if (anosEmpresa >= 10) {
            aumento = salarioBase * 0.1; // 10% de aumento para mais de 10 anos
        } else if (anosEmpresa >= 5) {
            aumento = salarioBase * 0.05; // 5% de aumento para mais de 5 anos
        }

        return salarioBase + aumento;
    }

    public String getNome() {
        return nome;
    }

    public static void main(String[] args) {
        Scanner snc = new Scanner(System.in);
        System.out.println("Digite o nome: ");
        String nome = snc.nextLine();
        System.out.println("Digite o Ano de admissão (Ano-Mes-Dia): ");
        String data = snc.nextLine();
        System.out.println("Digite o valor por hora deste funcionário: ");
        float salario_hora = snc.nextFloat();
        System.out.println("Digite o tempo trabalhado: ");
        float hora_trabalhada = snc.nextFloat();
        
        
        Funcionario funcionario = new Funcionario(nome, data, salario_hora, hora_trabalhada);
        int tempoEmpresa = funcionario.calcularTempoEmpresa();
        double salario = funcionario.calcularSalario();

        
        System.out.println("Funcionário: " + funcionario.getNome());
        System.out.println("Tempo de empresa: " + tempoEmpresa + " anos");
        System.out.println("Salário: R$" + salario);
    }
}
