/*
Чиликов Вадим Андреевич 1 курс, 1 группа.
Лабараторная работа номер 2 : Ряды.
Функция : у = 1/sqrt(1+x) , где |x| < 1 ;
          Ai =pow(-1,i) * ((2*i)!*pow(x,i))/(pow(pow(2,i)*i!),2),2))
Множитель: -x*(2 * i + 1) / (2 * i + 2) 
*/

#include <iostream>
#include <cmath>
#include <STDLIB.H>
using namespace std;

int main()
{
	char end_all = 'n';
	char end_al = 'q';
	setlocale(LC_ALL, "Russian");
	while (!((end_all == 'y') || (end_all == 'Y'))) // Зацикливаем всю прогу целиком.
	{
		double e;
		double x;
		double s = 0;
		double a = 1;
		int count;
		int choice;
		int number_of_slogans = 0;

		cout << "1. Сумма заданного значения. " << endl;
		cout << "2. Сумма с заданной точностью. " << endl;
		cout << "3. Заверщение работы. " << endl;
		cout << "-> ";
		cin >> choice;
		cout << "\n";
		
		while (!((choice == 1) || (choice == 2) || (choice == 3)))    // Цикл проверки вводимых значений.
		{
			cout << " Ошибка ввода, значение должно быть в интервале 1..3 . " << endl;
			cout << "-> ";
			cin >> choice;
			cout << "\n";
		}

		if (choice == 3)
			break;

		cout << " Значение Х: ";
		cin >> x;

		while (fabs(x) >= 1)         // Цикл проверки вводимых значений.
		{
			cout << " Ошибка ввода, значение должно быть в интервале -1..1, не включая крайние значения. " << endl;
			cout << "->";
			cin >> x;
			cout << "\n";
		}

		double current_value = 1 / sqrt(1 + x);

		if (choice == 1)                      // Считаем сумму заданного числа слагаемых.
		{
			cout << " Количество слогаемых: ";
			cin >> count;
			cout << "\n";
			int i = 0;
			while (i < count)
			{
				s = s + a;
				a = a*-x*(2 * i + 1) / (2 * i + 2);
				++i;
			}
			cout << " Точное значение       = " << current_value << endl;
			cout << " Приближенное значение = " << s << endl;
			cout << "\n";
			while (!((end_al == 'n') || (end_al == 'N') || (end_al == 'y') || (end_al == 'Y')))
			{
				cout << " Завершить работу? (Y/N) ";
				cout << " -> ";
				cin >> end_al;
				cout << "\n\n";
			}
			if ((end_al == 'y') || (end_al == 'Y'))
			break;
			end_al = 'p';
		}

		if (choice == 2)
		{
			cout << " Точность Е = ";
			cin >> e;
			cout << "\n";
			while (fabs(current_value - s) > e)
			{
				s = s + a;
				a = a*-x*(2 * number_of_slogans + 1) / (2 * number_of_slogans + 2);
				number_of_slogans += 1;
			}
			cout << " Точное значение       = " << current_value << endl;
			cout << " Приближенное значение = " << s << endl;
			cout << " Число слагаемых       = " << number_of_slogans << endl;
			cout << "\n";
			while (!((end_al == 'n') || (end_al == 'N') || (end_al == 'y') || (end_al == 'Y')))
			{
				cout << " Завершить работу? (Y/N) ";
				cout << " -> ";
				cin >> end_al;
				cout << "\n\n";
			}
			if ((end_al == 'y') || (end_al == 'Y'))
				break;
			end_al = 'p';
		}
	}
	return 0;

}
