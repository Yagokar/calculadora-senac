# calculadora-senac

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;


namespace senac.calculadora
{
    public partial class Form1 : Form
    {
        decimal numero1, numero2;
        string operacao = "";
        public Form1()
        {
            InitializeComponent();
        }

        public void InsereNumero(int numero)
        {
            if (textBoxresultado.Text == "0")
            {
                textBoxresultado.Clear();
            }
            textBoxresultado.Text = textBoxresultado.Text + numero;
        }

        private void Buttonum_Click(object sender, EventArgs e)
        {
            InsereNumero(1);
        }

        private void Buttondois_Click(object sender, EventArgs e)
        {
            if (textBoxresultado.Text == "0")
            {
                textBoxresultado.Clear();
            }
            textBoxresultado.Text = textBoxresultado.Text + "1";
        }


        public decimal Soma(decimal valor1, decimal valor2)
        {
            decimal resultado = valor1 + valor2;
            return resultado;
        }

        public decimal Subtrai(decimal valor1, decimal valor2)
        {
            decimal resultado = valor1 - valor2;
            return resultado;
        }
        public decimal Multiplica(decimal valor1, decimal valor2)
        {
            decimal resultado = valor1 * valor2;
            return resultado;
        }
        public decimal Divide(decimal valor1, decimal valor2)
        {
            decimal resultado = valor1 / valor2;

            if (valor2 == 0)
            {
                MessageBox.Show("ERRO");
                return 0;
            }
            return resultado;
        }
        public decimal efetuaquadrado(decimal valor1)
        {
            decimal resultado = valor1 * valor1;
            return resultado;
        }
        public void GeraResultado()
        {
            decimal resultado = 0;
            switch (operacao)
            {
                case "+":
                    resultado = Soma(numero1, numero2);
                    break;
                case "-":
                    resultado = Subtrai(numero1, numero2);
                    break;
                case "*":
                    resultado = Multiplica(numero1, numero2);
                    break;
                case "/":
                    resultado = Divide(numero1, numero2);
                    break;
                case "2":
                    resultado = efetuaquadrado(numero1);
                    break;
                case "%":
                    resultado = numero1 * (numero2 / 100);
                    break;
                   
            }
            textBoxresultado.Text = resultado.ToString();

            labelhistorico.Text = "" + numero2 + "=" + resultado;

            if(operacao == "%")
            {
                labelhistorico.Text += numero2 + "% de " + numero1 + " = " + resultado;
            }
        }
        public void GerarOperacao(string op)
        {
            if (operacao != "")
            {
                numero2 = Convert.ToDecimal(textBoxresultado);
            }
            operacao = op;
            numero1 = Convert.ToDecimal(textBoxresultado.Text);
            textBoxresultado.Text = "0";
        }


        private void buttonZero_Click(object sender, EventArgs e)
        {
            InsereNumero(0);
        }

        private void buttonUm_Click_1(object sender, EventArgs e)
        {
            InsereNumero(1);
        }

        private void buttonDois_Click_1(object sender, EventArgs e)
        {
            InsereNumero(2);
        }

        private void buttonTres_Click(object sender, EventArgs e)
        {
            InsereNumero(3);
        }

        private void buttonQuatro_Click(object sender, EventArgs e)
        {
            InsereNumero(4);
        }

        private void buttonCinco_Click(object sender, EventArgs e)
        {
            InsereNumero(5);
        }

        private void buttonSeis_Click(object sender, EventArgs e)
        {
            InsereNumero(6);
        }

        private void buttonSete_Click(object sender, EventArgs e)
        {
            InsereNumero(7);
        }

        private void buttonOito_Click(object sender, EventArgs e)
        {
            InsereNumero(8);
        }

        private void buttonNove_Click(object sender, EventArgs e)
        {
            InsereNumero(9);
        }

        private void buttonSoma_Click_1(object sender, EventArgs e)
        {
            GerarOperacao("+");
        }

        private void buttonLimpa_Click(object sender, EventArgs e)
        {
            numero1 = 0;
            numero2 = 0;
            textBoxresultado.Text = "0";
            operacao = "";
            labelhistorico.Text = "";
        }

        private void buttonSubtrai_Click(object sender, EventArgs e)
        {
            GerarOperacao("-");
        }

        private void buttonMultiplica_Click(object sender, EventArgs e)
        {
            GerarOperacao("*");
        }

        private void buttonDivide_Click(object sender, EventArgs e)
        {
            GerarOperacao("/");
        }

        private void buttonResultado_Click(object sender, EventArgs e)
        {
            numero2 = Convert.ToDecimal(textBoxresultado.Text);
            GeraResultado();
        }

        private void buttonPonto_Click(object sender, EventArgs e)
        {
            if (!textBoxresultado.Text.Contains(","))
            {
                textBoxresultado.Text = textBoxresultado.Text + ",";
            }
        }

        private void buttonQuadrado_Click(object sender, EventArgs e)
        {
            numero1 = Convert.ToDecimal(textBoxresultado.Text);
            operacao = "2";
            GeraResultado();

            labelhistorico.Text = "quadrado de" + numero1 + " = " + textBoxresultado.Text;
        }

        private void buttonPercentual_Click(object sender, EventArgs e)
        {
            GerarOperacao("%");
        }
    }

}

            
