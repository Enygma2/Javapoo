# Javapoo
Atividade 01 
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
package com.mycompany.atividade1;

public class Atividade1 {
    public static void main(String[] args) {
        System.out.println("Atividade 01!");
        TestaVeiculos.main(args);
        System.out.println("\n=== TESTE ALTERNATIVO ===");
        Carro meuCarro = new Carro("porsche 911", 2020, 2);
        Moto minhaMoto = new Moto("Titan", 2021, 150);
        
        meuCarro.acelerar(60);
        minhaMoto.acelerar(40);
        
        meuCarro.exibirInformacoes();
        minhaMoto.exibirInformacoes();
    }
}
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
package com.mycompany.atividade1;

public class Carro extends Veiculos {
    private int portas;

    public Carro(String modelo, int ano, int portas) {
        super(modelo, ano);
        this.portas = portas;
    }

    public void abrirPorta() {
        System.out.println("Porta do carro " + modelo + " aberta");
    }

    @Override
    public void exibirInformacoes() {
        super.exibirInformacoes();
        System.out.println("Número de portas: " + portas);
    }
}
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
package com.mycompany.atividade1;

public class Moto extends Veiculos {
    private int cilindradas;

    public Moto(String modelo, int ano, int cilindradas) {
        super(modelo, ano);
        this.cilindradas = cilindradas;
    }

    public void empinar() {
        if (velocidade > 30) {
            System.out.println("Moto " + modelo + " empinando!");
        } else {
            System.out.println("Velocidade muito baixa para empinar");
        }
    }

    @Override
    public void exibirInformacoes() {
        super.exibirInformacoes();
        System.out.println("Cilindradas: " + cilindradas + "cc");
    }
}
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

package com.mycompany.atividade1;


public class TestaVeiculos {
    public static void main(String[] args) {
        Carro carro = new Carro("Supra", 2020, 2);
        Moto moto = new Moto("CB500", 2023, 500);
        
        // Teste básico
        System.out.println("=== TESTE INICIAL ===");
        carro.exibirInformacoes();
        System.out.println();
        moto.exibirInformacoes();
        
        // Teste de aceleração
        System.out.println("\n=== TESTE DE ACELERAÇÃO ===");
        carro.acelerar(70);
        moto.acelerar(100);
        
        // Teste de frenagem
        System.out.println("\n=== TESTE DE FREIO ===");
        carro.frear(20);
        moto.frear(40); // Testando frenagem excessiva
        
        // Teste de métodos específicos
        System.out.println("\n=== TESTE DE MÉTODOS ESPECÍFICOS ===");
        carro.abrirPorta();
        moto.empinar();
        
        // Teste de moto parada
        System.out.println("\n=== TESTE MOTO PARADA ===");
        Moto motoParada = new Moto("Pop100", 2020, 100);
        motoParada.empinar(); // Não deve empinar
    }
}
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
package com.mycompany.atividade1;

public abstract class Veiculos {
    protected String modelo;
    protected int ano;
    protected double velocidade;

    public Veiculos(String modelo, int ano) {
        this.modelo = modelo;
        this.ano = ano;
        this.velocidade = 0;
    }

    public void acelerar(double incremento) {
        this.velocidade += incremento;
        System.out.println(modelo + " acelerando para " + velocidade + " km/h");
    }

    public void frear(double decremento) {
        if (velocidade - decremento < 0) {
            System.out.println("ERRO: Não pode frear abaixo de 0 km/h");
            velocidade = 0;
        } else {
            velocidade -= decremento;
        }
        System.out.println(modelo + " freando para " + velocidade + " km/h");
    }

    public void exibirInformacoes() {
        System.out.println("Modelo: " + modelo);
        System.out.println("Ano: " + ano);
        System.out.println("Velocidade atual: " + velocidade + " km/h");
    }
}
