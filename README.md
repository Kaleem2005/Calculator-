# Calculator-



import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class Calculator implements ActionListener {
    
    JFrame frame;
    JTextField textfield;
    JButton[] numberButtons = new JButton[10];
    JButton []functionbuttons = new JButton[9];
    JButton addButton, subButton, mulButton, divButton;
    JButton decButton, equButton, delButton, clrButton, negButton;
    JPanel panel;
    
    Font myFont = new Font ("Int Free", Font.BOLD, 30);
    Font myfont = new Font ("Ink Free", Font.PLAIN, 30);
    
    double num1 = 0,num2 = 0;
    double result = 0;
    char operator;
    
    @SuppressWarnings("static-access")
	Calculator () {
           
        frame = new JFrame("Calculator");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);                           // for open and close
        frame.setSize(405, 532);                                                         
        frame.setLayout(null);                                                           
        frame.setBackground(null);
        frame.setResizable(false);
        
        textfield = new JTextField();
        textfield.setBounds(50, 25 ,300, 50);
        textfield.setFont(myFont);
        textfield.setEditable(true);
        textfield.setBackground(null);
        textfield.setBorder(null);
        textfield.setHorizontalAlignment(textfield.RIGHT);

        addButton = new JButton("+");
        subButton = new JButton("-");
        mulButton = new JButton("x");
        divButton = new JButton("÷");
        decButton = new JButton(".");
        equButton = new JButton("=");
        delButton = new JButton("Delete");
        clrButton = new JButton("Clear");
        negButton = new JButton("(-)");
        
        
        functionbuttons[0] = addButton;
        functionbuttons[1] = subButton;
        functionbuttons[2] = mulButton;
        functionbuttons[3] = divButton;
        functionbuttons[4] = decButton;
        functionbuttons[5] = equButton;
        functionbuttons[6] = delButton;
        functionbuttons[7] = clrButton;
        functionbuttons[8] = negButton;
        
        
        for(int i = 0; i < 9; i++) {
        	
            functionbuttons[i].addActionListener(this);
            functionbuttons[i].setFont(myfont);
            functionbuttons[i].setFocusable(false);
            functionbuttons[i].setBackground(Color.lightGray);
        }
        
         for(int i = 0; i < 10; i++) {
        	 
           numberButtons[i] = new JButton(String.valueOf(i));
           numberButtons[i].addActionListener(this);
           numberButtons[i].setFont(myfont);
           numberButtons[i].setFocusable(false);
           numberButtons[i].setBackground(Color.white);
        }
         
         negButton.setBounds(50,430,100,50);
         delButton.setBounds(150,430,100,50);
         clrButton.setBounds(250,430,100,50);
        
         panel = new JPanel();
         panel.setBounds(50 , 100 , 300, 300);
         panel.setLayout(new GridLayout (4, 4, 10,10));
         panel.setBackground(null);
         

         frame.add(panel);
         panel.add(numberButtons[1]);
         panel.add(numberButtons[2]);
         panel.add(numberButtons[3]);
         panel.add(addButton);
         panel.add(numberButtons[4]);
         panel.add(numberButtons[5]);
         panel.add(numberButtons[6]);
         panel.add(subButton);
         panel.add(numberButtons[7]);
         panel.add(numberButtons[8]);
         panel.add(numberButtons[9]);
         panel.add(mulButton);
         panel.add(decButton);
         panel.add(numberButtons[0]);
         panel.add(equButton);
         panel.add(divButton);
         
        frame.add(panel);
        frame.add(negButton);
        frame.add(delButton);
        frame.add(clrButton);											// Adding into frame
        frame.add(textfield);
        frame.setVisible(false);
    }
   
	public static void main(String[] args) {

        Calculator calc = new Calculator();
    }
    
    @Override
    public void actionPerformed(ActionEvent e) {
        
        for(int i = 0; i < 10; i++) {
            if(e.getSource() == numberButtons[i]) {
                textfield.setText(textfield.getText().concat(String.valueOf(i)));
            }
        }
        
        if(e.getSource() == decButton) {
            textfield.setText(textfield.getText().concat("."));
        }
        if(e.getSource() == addButton) {
            num1 = Double.parseDouble(textfield.getText());
            operator = '+';
            textfield.setText("");
        }
         if(e.getSource() == subButton) {
            num1 = Double.parseDouble(textfield.getText());
            operator = '-';
            textfield.setText("");
        }
         if(e.getSource() == mulButton) {
            num1 = Double.parseDouble(textfield.getText());
            operator = '*';
            textfield.setText("");
        }
          if(e.getSource() == divButton) {
            num1 = Double.parseDouble(textfield.getText());
            operator = '/';
            textfield.setText("");
        }
          if(e.getSource() == equButton) {
              num2 = Double.parseDouble(textfield.getText());
              switch(operator) {
                  case'+':
                      result = num1 + num2;
                      break;
                  case'-':
                      result = num1 - num2;
                      break;
                  case'*':
                      result = num1 * num2;
                          break;
                  case'/':
                      result = num1 / num2;
                          break;
                          
              }
              textfield.setText(String.valueOf(result));
              num1=result;
          }
          if(e.getSource() == clrButton) {
            textfield.setText("");
        }
          if(e.getSource() == delButton) {
              String delete = textfield.getText();
              textfield.setText("");
              for(int i=0; i<delete.length()-1 ;i++) {
                  textfield.setText(textfield.getText() + delete.charAt(i));
              }
          }
          if(e.getSource() == negButton) {
             double neg = Double.parseDouble(textfield.getText());
             neg*=-1;
             textfield.setText(String.valueOf(neg));
          }
    }
    
}
