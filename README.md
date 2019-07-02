# RSA
#include "pch.h"
#include <iostream>
#include <math.h>

using namespace std;


int main()
{
	setlocale(LC_ALL, "Russian");
	int p, q, e;
	unsigned long long  E1, E2;
	cout << "Введите простое число p" << endl;
	cin >> p;
	cout << "Введите простое число q" << endl;
	cin >> q;
	cout << "Введите число " << endl;
	cin >> E1;
	int n = p * q;
	int f = (p - 1)*(q - 1);
	int cnst = 0;
	while (cnst != 1)
	{
		if ((f % 2) == 1)
		{
			e = 2;
			cnst = 1;
		}
		if ((f % 2) == 0)
		{
			e = 3;
			cnst = 1;
		} 
	}
	cnst = 0;
	cout << "Открытый ключ - {" << e << ',' << n << '}' << endl;
	E2 = pow(E1, e);
	E2 = E2 % n;
	cout << "Зашифрованное сообщение " << E2 << endl;
	int d=1;
	int z = 0;
	while (z != 1)
	{
		d++;
		z = (d*e) % f;
	}

	E1 = pow(E2, d);
	E1 = E1 % n;
	cout << "Закрытый ключ - {" << d << ',' << n << '}' << endl;
	cout << "Расшифрованное сообщение " << E1;
	
}
