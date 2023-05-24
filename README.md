using System;
using System.Collections.Generic;
using System.Windows;

namespace WpfApp1
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private void BtnCancelClick(object sender, RoutedEventArgs e)
        {
            Close();
        }

        private void BtnOKClick(object sender, RoutedEventArgs e)
        {
            try
            {
                int n = Convert.ToInt32(ListBoxData.Items[0]);
                List<int> sequence = new List<int>();

                for (int i = 1; i <= n; i++)
                {
                    int m = Convert.ToInt32(ListBoxData.Items[i]);
                    sequence.Add(m);
                }

                int count = CountNumbersDivisibleBy3AndEndingWith2(sequence);
                TextBlockAnswer.Text = $"Ответ:\n{count}";
            }
            catch (FormatException)
            {
                MessageBox.Show("Введены некорректные данные");
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
            }
        }

        private int CountNumbersDivisibleBy3AndEndingWith2(List<int> sequence)
        {
            int count = 0;

            foreach (int num in sequence)
            {
                if (num % 3 == 0 && num % 10 == 2)
                {
                    count++;
                }
            }

            return count;
        }

        private void BtnAdd_Click(object sender, RoutedEventArgs e)
        {
            if (!String.IsNullOrEmpty(TbNumber.Text))
            {
                try
                {
                    int xa = Convert.ToInt32(TbNumber.Text);
                    ListBoxData.Items.Add(xa);
                }
                catch (FormatException)
                {
                    MessageBox.Show("Введены некорректные данные");
                }
                catch (Exception ex)
                {
                    MessageBox.Show(ex.Message);
                }
            }
        }
    }
}
