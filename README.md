# exerciciosDTOVieweDAO

# Exercício 1: Formas Geométricas Abstratas

# a tela 

![telacalculogeometrico](https://github.com/user-attachments/assets/b713a14a-3f21-4274-aab5-3258423de4b7)


# codigo da tela 


import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
/**
 *
 * @author DOUGLAS VIEIRA
 */
public class FormaView extends javax.swing.JFrame {

    private FormaController controller;
    /**
     * Creates new form FormaView
     */
    public FormaView() {
        initComponents();
        controller = new FormaController();
        
          // Atualizar o comboFormas com as opções corretas
        comboFormas.setModel(new javax.swing.DefaultComboBoxModel<>(new String[] { "Círculo", "Retângulo", "Triângulo" }));
        
         // Configurar a ação do botão Calcular
        btnCalcular.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                calcularArea();
    }
                });
    }
    
     // Método para calcular a área da forma selecionada
    private void calcularArea() {
        String formaSelecionada = (String) comboFormas.getSelectedItem();
        FormaGeometrica forma = null;

        try {
            if (formaSelecionada.equals("Círculo")) {
                double raio = Double.parseDouble(JOptionPane.showInputDialog("Informe o raio do círculo:"));
                forma = new CirculoDTO(raio);

            } else if (formaSelecionada.equals("Retângulo")) {
                double largura = Double.parseDouble(JOptionPane.showInputDialog("Informe a largura do retângulo:"));
                double altura = Double.parseDouble(JOptionPane.showInputDialog("Informe a altura do retângulo:"));
                forma = new RetanguloDTO(largura, altura);

            } else if (formaSelecionada.equals("Triângulo")) {
                double base = Double.parseDouble(JOptionPane.showInputDialog("Informe a base do triângulo:"));
                double altura = Double.parseDouble(JOptionPane.showInputDialog("Informe a altura do triângulo:"));
                forma = new TrianguloDTO(base, altura);
            }

            if (forma != null) {
                controller.adicionarForma(forma);
                double area = forma.calcularArea();
                lblResultado.setText("Área: " + area);
            }

        } catch (NumberFormatException ex) {
            JOptionPane.showMessageDialog(this, "Por favor, insira valores numéricos válidos.", "Erro", JOptionPane.ERROR_MESSAGE);
        }
    }
    
      

    /**
     * This method is called from within the constructor to initialize the form.
     * WARNING: Do NOT modify this code. The content of this method is always
     * regenerated by the Form Editor.
     */
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">                          
    private void initComponents() {

        painel = new javax.swing.JPanel();
        comboFormas = new javax.swing.JComboBox<>();
        btnCalcular = new javax.swing.JButton();
        lblResultado = new javax.swing.JLabel();

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);

        comboFormas.setModel(new javax.swing.DefaultComboBoxModel<>(new String[] { "Círculo", "Retângulo", "Triângulo" }));

        btnCalcular.setText("Calcular");
        btnCalcular.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                btnCalcularActionPerformed(evt);
            }
        });

        lblResultado.setBackground(new java.awt.Color(102, 102, 0));

        javax.swing.GroupLayout painelLayout = new javax.swing.GroupLayout(painel);
        painel.setLayout(painelLayout);
        painelLayout.setHorizontalGroup(
            painelLayout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(javax.swing.GroupLayout.Alignment.TRAILING, painelLayout.createSequentialGroup()
                .addGap(0, 0, Short.MAX_VALUE)
                .addComponent(lblResultado, javax.swing.GroupLayout.PREFERRED_SIZE, 136, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addContainerGap(javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE))
            .addGroup(painelLayout.createSequentialGroup()
                .addGap(167, 167, 167)
                .addGroup(painelLayout.createParallelGroup(javax.swing.GroupLayout.Alignment.TRAILING)
                    .addComponent(btnCalcular)
                    .addComponent(comboFormas, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                .addContainerGap(159, Short.MAX_VALUE))
        );
        painelLayout.setVerticalGroup(
            painelLayout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(painelLayout.createSequentialGroup()
                .addGap(70, 70, 70)
                .addComponent(comboFormas, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addGap(41, 41, 41)
                .addComponent(btnCalcular)
                .addGap(35, 35, 35)
                .addComponent(lblResultado, javax.swing.GroupLayout.PREFERRED_SIZE, 25, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addContainerGap(86, Short.MAX_VALUE))
        );

        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(getContentPane());
        getContentPane().setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addComponent(painel, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addComponent(painel, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
        );

        pack();
    }// </editor-fold>                        

    private void btnCalcularActionPerformed(java.awt.event.ActionEvent evt) {                                            
        // TODO add your handling code here:
    }                                           

    /**
     * @param args the command line arguments
     */
    public static void main(String args[]) {
        /* Set the Nimbus look and feel */
        //<editor-fold defaultstate="collapsed" desc=" Look and feel setting code (optional) ">
        /* If Nimbus (introduced in Java SE 6) is not available, stay with the default look and feel.
         * For details see http://download.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html 
         */
        try {
            for (javax.swing.UIManager.LookAndFeelInfo info : javax.swing.UIManager.getInstalledLookAndFeels()) {
                if ("Nimbus".equals(info.getName())) {
                    javax.swing.UIManager.setLookAndFeel(info.getClassName());
                    break;
                }
            }
        } catch (ClassNotFoundException ex) {
            java.util.logging.Logger.getLogger(FormaView.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (InstantiationException ex) {
            java.util.logging.Logger.getLogger(FormaView.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (IllegalAccessException ex) {
            java.util.logging.Logger.getLogger(FormaView.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (javax.swing.UnsupportedLookAndFeelException ex) {
            java.util.logging.Logger.getLogger(FormaView.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        }
        //</editor-fold>

        /* Create and display the form */
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new FormaView().setVisible(true);
            
                
            
                
            }
        });
    }

    // Variables declaration - do not modify                     
    private javax.swing.JButton btnCalcular;
    private javax.swing.JComboBox<String> comboFormas;
    private javax.swing.JLabel lblResultado;
    private javax.swing.JPanel painel;
    // End of variables declaration                   
}

# class circulo

public class CirculoDTO extends FormaGeometrica {
    private double raio;

    public CirculoDTO (double raio) {
        this.raio = raio;
    }

    public double getRaio() {
        return raio;
    }

    public void setRaio(double raio) {
        this.raio = raio;
    }
    

    @Override
    public double calcularArea() {
        return Math.PI * raio * raio;
    }
}

# class triangulo



/**
 *
 * @author DOUGLAS VIEIRA
 */
public class TrianguloDTO extends FormaGeometrica {
    private double base;
    private double altura;

    public TrianguloDTO (double base, double altura) {
        this.base = base;
        this.altura = altura;
    }

    public void setBase(double base) {
        this.base = base;
    }

    public void setAltura(double altura) {
        this.altura = altura;
    }

    public double getBase() {
        return base;
    }

    public double getAltura() {
        return altura;
    }

    @Override
    public double calcularArea() {
        return (base * altura) / 2;
    }
}

# class retangulo 



/**
 *
 * @author DOUGLAS VIEIRA
 */
public class RetanguloDTO extends FormaGeometrica {
    private double largura;
    private double altura;

    public RetanguloDTO (double largura, double altura) {
        this.largura = largura;
        this.altura = altura;
    }

    public double getLargura() {
        return largura;
    }

    public double getAltura() {
        return altura;
    }

    public void setLargura(double largura) {
        this.largura = largura;
    }

    public void setAltura(double altura) {
        this.altura = altura;
    }
    

    @Override
    public double calcularArea() {
        return largura * altura;
    }
}

# class forma controller 


import java.util.List;



/**
 *
 * @author Joel
 */
public class FormaController {
    private FormaDAO formaDAO;

    public FormaController() {
        formaDAO = new FormaDAO();
    }

    public void adicionarForma(FormaGeometrica forma) {
        formaDAO.salvarForma(forma);
    }

    public List<FormaGeometrica> listarFormas() {
        return formaDAO.listarFormas();
    }
}

# class forma DAO 




/**
 *
 * @author DOUGLAS VIEIRA 
 */
import java.util.ArrayList;
import java.util.List;

public class FormaDAO {
    private List<FormaGeometrica> formas = new ArrayList<>();

    public void salvarForma(FormaGeometrica forma) {
        formas.add(forma);
    }

    public List<FormaGeometrica> listarFormas() {
        return formas;
    }
}

# CLASS FORMAGEOMETRICA 



/**
 *
 * @author DOUGLAS VIEIRA
 */
public abstract class FormaGeometrica {
    
     public abstract double calcularArea();
    
    
}

# exercicio 2 animais 

# tela 

![telaanimal](https://github.com/user-attachments/assets/d55ded26-5058-439e-832c-af44fb771602)


/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package View;

import DAO.AnimalDAO;
import DTO.AnimalDTO;
import DTO.CachorroDTO;
import DTO.GatoDTO;
import DTO.PassaroDTO;

import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

/**
 *
 * @author Joel
 */
public class AnimalView extends javax.swing.JFrame {

    private AnimalDAO animalDAO;
    private JComboBox<String> animalComboBox;
    private JTextField resultadoField;
    /**
     * Creates new form AnimalView
     * @param animalDAO
     */
    public AnimalView(AnimalDAO animalDAO) {
        initComponents();
        this.animalDAO = animalDAO;
        
        // Evento do botão Som
        btnSom.addActionListener((ActionEvent e) -> {
            emitirSom();
        });

        // Evento do botão Mover
        btnMover.addActionListener((ActionEvent e) -> {
            moverAnimal();
        });
    
        
        
        
        
    }

    private AnimalView() {
        throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
    }

    

    
    
       // Método para emitir som do animal
    private void emitirSom() {
        String tipoAnimal = (String) ComboBoxAnimal.getSelectedItem();
        AnimalDTO animal = criarAnimal(tipoAnimal);
        if (animal != null) {
            animalDAO.adicionarAnimal(animal);
            String som = animal.emitirSom();
            txtMensagem.setText(som);  // Exibe o som no TextField
            JOptionPane.showMessageDialog(this, som);  // Exibe no JOptionPane
        }
    }

    // Método para mover o animal
    private void moverAnimal() {
        String tipoAnimal = (String) ComboBoxAnimal.getSelectedItem();
        AnimalDTO animal = criarAnimal(tipoAnimal);
        if (animal != null) {
            animalDAO.adicionarAnimal(animal);
            String movimento = animal.mover();
            txtMensagem.setText(movimento);  // Exibe o movimento no TextField
            JOptionPane.showMessageDialog(this, movimento);  // Exibe no JOptionPane
        }
    }

    // Método que cria um animal com base na seleção
    private AnimalDTO criarAnimal(String tipo) {
        switch (tipo) {
            case "CACHORRO":
                return new CachorroDTO("Buddy");
            case "GATO":
                return new GatoDTO("Whiskers");
            case "PASSARO":
                return new PassaroDTO("Tweety");
            default:
                return null;
        }
    }

    /**
     * This method is called from within the constructor to initialize the form.
     * WARNING: Do NOT modify this code. The content of this method is always
     * regenerated by the Form Editor.
     */
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">                          
    private void initComponents() {

        txtMensagem = new javax.swing.JTextField();
        ComboBoxAnimal = new javax.swing.JComboBox<>();
        btnMover = new javax.swing.JButton();
        btnSom = new javax.swing.JButton();

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);

        txtMensagem.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                txtMensagemActionPerformed(evt);
            }
        });

        ComboBoxAnimal.setModel(new javax.swing.DefaultComboBoxModel<>(new String[] { "ANIMAL", "CACHORRO", "GATO", "PASSARO" }));

        btnMover.setText("MOVER");

        btnSom.setText("SOM");

        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(getContentPane());
        getContentPane().setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
                    .addGroup(layout.createSequentialGroup()
                        .addGap(146, 146, 146)
                        .addComponent(ComboBoxAnimal, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE))
                    .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.TRAILING)
                        .addGroup(javax.swing.GroupLayout.Alignment.LEADING, layout.createSequentialGroup()
                            .addGap(97, 97, 97)
                            .addComponent(btnMover)
                            .addGap(38, 38, 38)
                            .addComponent(btnSom))
                        .addGroup(layout.createSequentialGroup()
                            .addGap(109, 109, 109)
                            .addComponent(txtMensagem, javax.swing.GroupLayout.PREFERRED_SIZE, 167, javax.swing.GroupLayout.PREFERRED_SIZE))))
                .addContainerGap(124, Short.MAX_VALUE))
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addGap(33, 33, 33)
                .addComponent(txtMensagem, javax.swing.GroupLayout.PREFERRED_SIZE, 55, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addGap(18, 18, 18)
                .addComponent(ComboBoxAnimal, javax.swing.GroupLayout.PREFERRED_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.PREFERRED_SIZE)
                .addGap(44, 44, 44)
                .addGroup(layout.createParallelGroup(javax.swing.GroupLayout.Alignment.BASELINE)
                    .addComponent(btnMover)
                    .addComponent(btnSom))
                .addContainerGap(107, Short.MAX_VALUE))
        );

        pack();
    }// </editor-fold>                        

    private void txtMensagemActionPerformed(java.awt.event.ActionEvent evt) {                                            
        // TODO add your handling code here:
    }                                           

    /**
     * @param args the command line arguments
     */
    public static void main(String args[]) {
        /* Set the Nimbus look and feel */
        //<editor-fold defaultstate="collapsed" desc=" Look and feel setting code (optional) ">
        /* If Nimbus (introduced in Java SE 6) is not available, stay with the default look and feel.
         * For details see http://download.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html 
         */
        try {
            for (javax.swing.UIManager.LookAndFeelInfo info : javax.swing.UIManager.getInstalledLookAndFeels()) {
                if ("Nimbus".equals(info.getName())) {
                    javax.swing.UIManager.setLookAndFeel(info.getClassName());
                    break;
                }
            }
        } catch (ClassNotFoundException ex) {
            java.util.logging.Logger.getLogger(AnimalView.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (InstantiationException ex) {
            java.util.logging.Logger.getLogger(AnimalView.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (IllegalAccessException ex) {
            java.util.logging.Logger.getLogger(AnimalView.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (javax.swing.UnsupportedLookAndFeelException ex) {
            java.util.logging.Logger.getLogger(AnimalView.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        }
        //</editor-fold>

        /* Create and display the form */
        java.awt.EventQueue.invokeLater(() -> {
            new AnimalView().setVisible(true);
        });
    }

    // Variables declaration - do not modify                     
    private javax.swing.JComboBox<String> ComboBoxAnimal;
    private javax.swing.JButton btnMover;
    private javax.swing.JButton btnSom;
    private javax.swing.JTextField txtMensagem;
    // End of variables declaration                   
}



package DAO;

/**
 *
 * @author DOUGLAS VIEIRA
 */

// AnimalDAO.java
import DTO.AnimalDTO;
import java.util.ArrayList;
import java.util.List;

public class AnimalDAO {
    private List<AnimalDTO> animais;

    public AnimalDAO() {
        animais = new ArrayList<>();
    }

    public void adicionarAnimal(AnimalDTO animal) {
        animais.add(animal);
    }

    public List<AnimalDTO> listarAnimais() {
        return animais;
    }}

    



package DTO;

/**
 *
 * @author DOUGLAS VIEIRA
 */

// PassaroDTO.java
public class PassaroDTO extends AnimalDTO {
    public PassaroDTO(String nome) {
        super(nome);
    }

    @Override
    public String emitirSom() {
        return "O pássaro " + getNome() + " faz: Piu Piu!";
    }

    @Override
    public String mover() {
        return "O pássaro " + getNome() + " está voando.";
    }
}



package DTO;

/**
 *
 * @author DOUGLAS VIEIRA
 */
// GatoDTO.java
public class GatoDTO extends AnimalDTO {
    public GatoDTO(String nome) {
        super(nome);
    }

    @Override
    public String emitirSom() {
        return "O gato " + getNome() + " faz: Miau!";
    }

    @Override
    public String mover() {
        return "O gato " + getNome() + " está caminhando.";
    }
}



package DTO;

/**
 *
 * @author DOUGLAS VIEIRA 
 */


// CachorroDTO.java
public class CachorroDTO extends AnimalDTO {
    public CachorroDTO(String nome) {
        super(nome);
    }

    @Override
    public String emitirSom() {
        return "O cachorro " + getNome() + " faz: Au Au!";
    }

    @Override
    public String mover() {
        return "O cachorro " + getNome() + " está correndo.";
    }
}



package DTO;

/**
 *
 * @author DOUGLAS VIEIRA
 */

// AnimalDTO.java
public abstract class AnimalDTO {
    private String nome;

    public AnimalDTO(String nome) {
        this.nome = nome;
    }

    public String getNome() {
        return nome;
    }

    public void setNome(String nome) {
        this.nome = nome;
    }

    public abstract String emitirSom();
    public abstract String mover();
}

# exercicio 3

# codigo da tela 

package View;

import DAO.ContaBancariaDAO;
import DTO.ContaBancariaDTO;
import DTO.ContaCorrenteDTO;
import DTO.ContaPoupancaDTO;

import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class BancoView extends JFrame {
    private ContaBancariaDAO contaDAO;
    private JComboBox<String> tipoContaComboBox;
    private JTextField numeroContaField;

    public BancoView(ContaBancariaDAO contaDAO) {
        this.contaDAO = contaDAO;
        initComponents();
    }

    private void initComponents() {
        setTitle("Banco - Gerenciamento de Contas");
        setSize(400, 300);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        // ComboBox para selecionar tipo de conta
        String[] tiposConta = {"Conta Corrente", "Conta Poupança"};
        tipoContaComboBox = new JComboBox<>(tiposConta);

        // TextField para número da conta
        numeroContaField = new JTextField(10);

        // Botões
        JButton btnCriarConta = new JButton("Criar Conta");
        JButton btnSacar = new JButton("Sacar");
        JButton btnDepositar = new JButton("Depositar");

        // Layout
        JPanel panel = new JPanel();
        panel.add(new JLabel("Número da Conta:"));
        panel.add(numeroContaField);
        panel.add(tipoContaComboBox);
        panel.add(btnCriarConta);
        panel.add(btnSacar);
        panel.add(btnDepositar);
        add(panel);

        // Ações dos botões
        btnCriarConta.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                criarConta();
            }
        });

        btnSacar.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                realizarSaque();
            }
        });

        btnDepositar.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                realizarDeposito();
            }
        });
    }

    private void criarConta() {
        String numeroConta = numeroContaField.getText();
        String tipoConta = (String) tipoContaComboBox.getSelectedItem();
        ContaBancariaDTO conta;

        if (tipoConta.equals("Conta Corrente")) {
            conta = new ContaCorrenteDTO(numeroConta, 0);
        } else {
            conta = new ContaPoupancaDTO(numeroConta, 0);
        }

        contaDAO.adicionarConta(conta);
        JOptionPane.showMessageDialog(this, "Conta " + tipoConta + " criada com sucesso!");
    }

    private void realizarSaque() {
        String numeroConta = JOptionPane.showInputDialog("Digite o número da conta:");
        ContaBancariaDTO conta = contaDAO.buscarConta(numeroConta);

        if (conta != null) {
            double valor = Double.parseDouble(JOptionPane.showInputDialog("Digite o valor a sacar:"));
            if (conta.sacar(valor)) {
                JOptionPane.showMessageDialog(this, "Saque realizado com sucesso!");
            } else {
                JOptionPane.showMessageDialog(this, "Saldo insuficiente!");
            }
        } else {
            JOptionPane.showMessageDialog(this, "Conta não encontrada!");
        }
    }

    private void realizarDeposito() {
        String numeroConta = JOptionPane.showInputDialog("Digite o número da conta:");
        ContaBancariaDTO conta = contaDAO.buscarConta(numeroConta);

        if (conta != null) {
            double valor = Double.parseDouble(JOptionPane.showInputDialog("Digite o valor a depositar:"));
            conta.depositar(valor);
            JOptionPane.showMessageDialog(this, "Depósito realizado com sucesso!");
        } else {
            JOptionPane.showMessageDialog(this, "Conta não encontrada!");
        }
    }

    public static void main(String[] args) {
        ContaBancariaDAO contaDAO = new ContaBancariaDAO();
        new BancoView(contaDAO).setVisible(true);
    }
}


# tela 

![telaconta](https://github.com/user-attachments/assets/f57451b1-30a3-4c54-bda6-023833dde1ca)


package DAO;

import DTO.ContaBancariaDTO;
import java.util.ArrayList;
import java.util.List;

public class ContaBancariaDAO {
    private List<ContaBancariaDTO> contas;

    public ContaBancariaDAO() {
        contas = new ArrayList<>();
    }

    public void adicionarConta(ContaBancariaDTO conta) {
        contas.add(conta);
    }

    public ContaBancariaDTO buscarConta(String numeroConta) {
        for (ContaBancariaDTO conta : contas) {
            if (conta.getNumeroConta().equals(numeroConta)) {
                return conta;
            }
        }
        return null;
    }
}


package DTO;

public class ContaPoupancaDTO extends ContaBancariaDTO {

    public ContaPoupancaDTO(String numeroConta, double saldo) {
        super(numeroConta, saldo);
    }

    @Override
    public boolean sacar(double valor) {
        if (valor <= saldo) {
            saldo -= valor;
            return true;
        }
        return false;
    }

    @Override
    public void depositar(double valor) {
        saldo += valor;
    }
}


package DTO;

public class ContaCorrenteDTO extends ContaBancariaDTO {

    public ContaCorrenteDTO(String numeroConta, double saldo) {
        super(numeroConta, saldo);
    }

    @Override
    public boolean sacar(double valor) {
        if (valor <= saldo) {
            saldo -= valor;
            return true;
        }
        return false;
    }

    @Override
    public void depositar(double valor) {
        saldo += valor;
    }
}



package DTO;

public abstract class ContaBancariaDTO {
    protected String numeroConta;
    protected double saldo;

    public ContaBancariaDTO(String numeroConta, double saldo) {
        this.numeroConta = numeroConta;
        this.saldo = saldo;
    }

    public String getNumeroConta() {
        return numeroConta;
    }

    public double getSaldo() {
        return saldo;
    }

    public abstract boolean sacar(double valor);

    public abstract void depositar(double valor);
}


# exercicio 4 

# CODIGO DA TELA 

package View;

import DAO.PagamentoDAO;
import DTO.PagamentoDTO;
import DTO.PagamentoCartaoCreditoDTO;
import DTO.PagamentoBoletoDTO;

import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class PagamentoView extends JFrame {
    private JComboBox<String> pagamentoComboBox;
    private JTextField valorBaseField;
    private JButton calcularButton;

    private PagamentoDAO pagamentoDAO;

    public PagamentoView(PagamentoDAO pagamentoDAO) {
        this.pagamentoDAO = pagamentoDAO;
        initUI();
    }

    private void initUI() {
        setTitle("Sistema de Pagamento");
        setSize(400, 200);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        String[] metodosPagamento = {"Cartão de Crédito", "Boleto"};
        pagamentoComboBox = new JComboBox<>(metodosPagamento);
        valorBaseField = new JTextField(10);

        calcularButton = new JButton("Calcular Pagamento");

        JPanel panel = new JPanel();
        panel.add(new JLabel("Método de Pagamento:"));
        panel.add(pagamentoComboBox);
        panel.add(new JLabel("Valor Base:"));
        panel.add(valorBaseField);
        panel.add(calcularButton);

        add(panel);

        calcularButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                calcularPagamento();
            }
        });
    }

    private void calcularPagamento() {
        String tipoPagamento = (String) pagamentoComboBox.getSelectedItem();
        double valorBase = Double.parseDouble(valorBaseField.getText());

        PagamentoDTO pagamento = null;
        switch (tipoPagamento) {
            case "Cartão de Crédito":
                double taxaJuros = Double.parseDouble(JOptionPane.showInputDialog("Informe a taxa de juros (%):"));
                pagamento = new PagamentoCartaoCreditoDTO(valorBase, taxaJuros);
                break;
            case "Boleto":
                double taxaBoleto = Double.parseDouble(JOptionPane.showInputDialog("Informe a taxa do boleto:"));
                pagamento = new PagamentoBoletoDTO(valorBase, taxaBoleto);
                break;
        }

        if (pagamento != null) {
            pagamentoDAO.adicionarPagamento(pagamento);
            JOptionPane.showMessageDialog(this, "Valor calculado: " + pagamento.calcularValor());
        }
    }

    public static void main(String[] args) {
        PagamentoDAO pagamentoDAO = new PagamentoDAO();
        PagamentoView view = new PagamentoView(pagamentoDAO);
        view.setVisible(true);
    }
}



# TELA 

![telapagamento](https://github.com/user-attachments/assets/2ef1a264-526b-4662-a6c7-0a175aa4614a)

# PAGAMENTODAO

package DAO;

import DTO.PagamentoDTO;
import java.util.ArrayList;
import java.util.List;

public class PagamentoDAO {
    private List<PagamentoDTO> pagamentos = new ArrayList<>();

    public void adicionarPagamento(PagamentoDTO pagamento) {
        pagamentos.add(pagamento);
    }

    public List<PagamentoDTO> getPagamentos() {
        return pagamentos;
    }
}


# PagamentoBoletoDTO 

package DTO;

public class PagamentoBoletoDTO extends PagamentoDTO {
    private double taxa;

    public PagamentoBoletoDTO(double valorBase, double taxa) {
        super(valorBase);
        this.taxa = taxa;
    }

    @Override
    public double calcularValor() {
        return valorBase + taxa;
    }
}


# PagamentoCartaoCreditoDTO

package DTO;

public class PagamentoCartaoCreditoDTO extends PagamentoDTO {
    private double taxaJuros;

    public PagamentoCartaoCreditoDTO(double valorBase, double taxaJuros) {
        super(valorBase);
        this.taxaJuros = taxaJuros;
    }

    @Override
    public double calcularValor() {
        return valorBase + (valorBase * taxaJuros / 100);
    }
}


# PagamentoDTO

package DTO;

public abstract class PagamentoDTO {
    protected double valorBase;

    public PagamentoDTO(double valorBase) {
        this.valorBase = valorBase;
    }

    public abstract double calcularValor();
}


# Exercício 5 

# codigo da tela

package View;

import DAO.FuncionarioDAO;
import DTO.FuncionarioDTO;
import DTO.GerenteDTO;
import DTO.ProgramadorDTO;

import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class FuncionarioView extends JFrame {
    private JComboBox<String> funcionarioComboBox;
    private JTextField salarioBaseField;
    private JButton calcularButton;

    private FuncionarioDAO funcionarioDAO;

    public FuncionarioView(FuncionarioDAO funcionarioDAO) {
        this.funcionarioDAO = funcionarioDAO;
        initUI();
    }

    private void initUI() {
        setTitle("Sistema de Funcionários");
        setSize(400, 200);
        setDefaultCloseOperation(EXIT_ON_CLOSE);
        setLocationRelativeTo(null);

        String[] tiposFuncionario = {"Gerente", "Programador"};
        funcionarioComboBox = new JComboBox<>(tiposFuncionario);
        salarioBaseField = new JTextField(10);

        calcularButton = new JButton("Calcular Salário");

        JPanel panel = new JPanel();
        panel.add(new JLabel("Tipo de Funcionário:"));
        panel.add(funcionarioComboBox);
        panel.add(new JLabel("Salário Base:"));
        panel.add(salarioBaseField);
        panel.add(calcularButton);

        add(panel);

        calcularButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                calcularSalario();
            }
        });
    }

    private void calcularSalario() {
        String tipoFuncionario = (String) funcionarioComboBox.getSelectedItem();
        double salarioBase = Double.parseDouble(salarioBaseField.getText());

        FuncionarioDTO funcionario = null;
        switch (tipoFuncionario) {
            case "Gerente":
                double bonusGerente = Double.parseDouble(JOptionPane.showInputDialog("Informe o bônus do gerente:"));
                funcionario = new GerenteDTO(salarioBase, bonusGerente);
                break;
            case "Programador":
                double bonusProgramador = Double.parseDouble(JOptionPane.showInputDialog("Informe o bônus do programador:"));
                funcionario = new ProgramadorDTO(salarioBase, bonusProgramador);
                break;
        }

        if (funcionario != null) {
            funcionarioDAO.adicionarFuncionario(funcionario);
            JOptionPane.showMessageDialog(this, "Salário calculado: " + funcionario.calcularSalario());
        }
    }

    public static void main(String[] args) {
        FuncionarioDAO funcionarioDAO = new FuncionarioDAO();
        FuncionarioView view = new FuncionarioView(funcionarioDAO);
        view.setVisible(true);
    }
}

# tela 

![funcionario](https://github.com/user-attachments/assets/ac925c2f-4323-45bd-a337-28908aca8946)


# FuncionarioDAO

package DAO;

import DTO.FuncionarioDTO;
import java.util.ArrayList;
import java.util.List;

public class FuncionarioDAO {
    private List<FuncionarioDTO> funcionarios = new ArrayList<>();

    public void adicionarFuncionario(FuncionarioDTO funcionario) {
        funcionarios.add(funcionario);
    }

    public List<FuncionarioDTO> getFuncionarios() {
        return funcionarios;
    }
}


# ProgramadorDTO

package DTO;

public class ProgramadorDTO extends FuncionarioDTO {
    private double bonus;

    public ProgramadorDTO(double salarioBase, double bonus) {
        super(salarioBase);
        this.bonus = bonus;
    }

    @Override
    public double calcularSalario() {
        return salarioBase + bonus;
    }
}


# GerenteDTO 

package DTO;

public class GerenteDTO extends FuncionarioDTO {
    private double bonus;

    public GerenteDTO(double salarioBase, double bonus) {
        super(salarioBase);
        this.bonus = bonus;
    }

    @Override
    public double calcularSalario() {
        return salarioBase + bonus;
    }
}


# FuncionarioDTO


package DTO;

public abstract class FuncionarioDTO {
    protected double salarioBase;

    public FuncionarioDTO(double salarioBase) {
        this.salarioBase = salarioBase;
    }

    public abstract double calcularSalario();
}















