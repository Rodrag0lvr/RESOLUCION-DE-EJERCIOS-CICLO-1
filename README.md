EJERCICIO QUINOA ESPECIAL

#include "pch.h"
#include <iostream>
using namespace std;
using namespace System;
void generar(char** quinoas);
void mayorymenorfrecuencia(char** quinoas);
void quinoaespecial(char** quinoas);

int main()
{
    char** quinoas = new char*[10];//filas
	for (int i = 0; i < 10; i++)
	{

		quinoas[i] = new char[15];
	}
	 generar( quinoas);
	 mayorymenorfrecuencia( quinoas);
	 quinoaespecial(quinoas);

	 for (int i = 0; i < 10; i++)
	 {

		 delete[] quinoas[i];
	 }

	 delete[] quinoas;

	 system("pause");
    return 0;
}void generar(char** quinoas) {
	char tipo[3] = { 'R','N','B' };
	Random random;
	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j < 15; j++)
		{
			quinoas[i][j] = tipo[random.Next(0, 3)];

		}

	}
	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j < 15; j++)
		{
			cout << "[" << quinoas[i][j] << "]" << " ";

		}
		cout << endl;
	}


}
void mayorymenorfrecuencia(char** quinoas) {
	int cR = 0, cN = 0, cB = 0;


	for (int i = 0; i < 10; i++)
	{
		for (int j = 0; j < 15; j++)
		{
			if (quinoas[i][j] == 'R') {
				cR++;
			}if (quinoas[i][j] == 'N') {
				cN++;
			}if (quinoas[i][j] == 'B') {
				cB++;
			}
		}
	}

	if (cR > cN && cR > cB ) {
		cout << "La mayor frecuencia es R" << endl;
	}
	else if (cR < cN && cN > cB ) {
		cout << "La mayor frecuencia es N" << endl;
	}
	else {
		cout << "La mayor frecuencia es B" << endl;
	}
	
	//MENOR FRECUENCIA
	if (cR < cN && cR <cB ) {
		cout << "La menor frecuencia es R" << endl;
	}
	else if (cR > cN && cN < cB ) {
		cout << "La menor frecuencia es N" << endl;
	}
	else  {
		cout << "La menor frecuencia es B" << endl;
	}
	

}
void quinoaespecial(char** quinoas) {
	bool encontrado = false;
	for (int i = 1; i < 9; i++)
	{
		for (int j = 1; j < 14; j++)
		{
			if (quinoas[i - 1][j - 1] == 'B' && quinoas[i - 1][j] == 'R' &&
				quinoas[i - 1][j + 1] == 'B' && quinoas[i + 1][j - 1] == 'N' &&
				quinoas[i + 1][j] == 'R' && quinoas[i + 1][j + 1] == 'N')
			{

				quinoas[i][j] = 'E';

				cout << "Se encontró un especial en el fila :" << i + 1 << endl;
				cout << " y en la columna " << j + 1 << endl;

				encontrado = true;
			}
		}
	}
	if (encontrado) {
		for (int i = 0; i < 10; i++)
		{
			for (int j = 0; j < 15; j++)
			{
				cout << "[" << quinoas[i][j] << "]" << " ";

			}
			cout << endl;
		}



	}




}
