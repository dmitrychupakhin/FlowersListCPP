#include <iostream>
#include <fstream>
#include <Windows.h>
#include <string>
#include <stdlib.h>

//Лабораторная работа 2
//Чупахин Дмитрий Алексеевич ПИ-22-1

using namespace std;

string path;

class flowers {
public:
	string name = "name";
	int price = 0;
};

void menu();
void menu(flowers* flowerForMenu, int numOfFlowers);
void open();
void add(flowers* flower, int numOfFlowers);
void print(flowers *flower, int numOfFlowers);
void printForDelete(flowers* flower, int numOfFlowers);
void calculation(flowers* flower,int numOfFlowers);
void del(flowers* flower, int numOfFlowers);
void save(flowers* flower, int numOfFlowers);
int inputInt(int min, int max);
void clear();

int main() {
	SetConsoleCP(1251);
	SetConsoleOutputCP(1251);

	menu();
	return 0;
}

void menu() {
	clear();
	cout << "*** Программа для обработки массива данных с цветами ***" << endl;
	cout << "1 - Открыть файл" << endl;
	cout << "2 - Вывести массив на экран" << endl;
	cout << "3 - Самый дешевый цветок" << endl;
	cout << "4 - Добавить элемент" << endl;
	cout << "5 - Удалить элемент" << endl;
	cout << "6 - Сохранить массив" << endl;
	cout << "7 - Закрыть программу" << endl;
	int choice;
	for (;;) {
		choice = inputInt(1, 7);
		switch (choice) {
		case 1:
			open();
		case 2:
			cout << "Откройте файл!" << endl;
			system("pause");
			menu();
		case 3:
			cout << "Откройте файл!" << endl;
			system("pause");
			menu();
		case 4:
			cout << "Откройте файл!" << endl;
			system("pause");
			menu();
			cout << "Откройте файл!" << endl;
			system("pause");
		case 5:
			menu();
			cout << "Откройте файл!" << endl;
			system("pause");
		case 6:
			menu();
			cout << "Откройте файл!" << endl;
			system("pause");
		case 7:
			clear();
			exit(0);
		}
	}
}


void menu(flowers *flower, int numOfFlowers) {
	clear();
	cout << "*** Программа для обработки массива данных с цветами ***" << endl;
	cout << "1 - Открыть файл" << endl;
	cout << "2 - Вывести массив на экран" << endl;
	cout << "3 - Самый дешевый цветок" << endl;
	cout << "4 - Добавить элемент" << endl;
	cout << "5 - Удалить элемент" << endl;
	cout << "6 - Сохранить массив" << endl;
	cout << "7 - Закрыть программу" << endl;
	int choice;
	for (;;) {
		choice = inputInt(1, 7);
		switch (choice) {
		case 1:
			open();
		case 2:
			print(flower, numOfFlowers);
		case 3:
			calculation(flower, numOfFlowers);
		case 4:
			add(flower, numOfFlowers);
		case 5:
			del(flower, numOfFlowers);
		case 6:
			save(flower, numOfFlowers);
		case 7:
			clear();
			exit(0);
		}
	}
}

void open() {
	clear();
	fstream file;
	while (!file.is_open()) {
		clear();
		cout << "Введите путь к файлу: ";
		cin.clear();
		cin.ignore(cin.rdbuf()->in_avail()); 
		getline(cin, path);
		file.open(path);
		if (!file.is_open()) {
			cout << "Файл не открыт" << endl;
			system("pause");
		}
		else {
			cout << "Файл открыт" << endl;
			system("pause");
		}
	}

	//Подсчет строк
	int NumOfLines = 0;
	string aLineStr;
	while (getline(file, aLineStr))
	{
		if (!aLineStr.empty())
			NumOfLines++;
	}

	file.clear();
	file.seekg(0, ios_base::beg);

	int numOfFlowers = NumOfLines / 2;

	flowers* flower = new flowers[numOfFlowers];

	for (int i = 0; !file.eof(); i++) {
		file >> flower[i].name;
		file >> flower[i].price;
	}

	file.close();

	menu(flower, numOfFlowers);
}

void add(flowers* flower, int numOfFlowers) {
	clear();
	flowers* someFlowers = new flowers[numOfFlowers + 1];
	for (int i = 0; i < numOfFlowers; i++) {
		someFlowers[i].name = flower[i].name;
		someFlowers[i].price = flower[i].price;
	}
	cout << "Введите название комнатного цветка: ";
	cin.clear();
	cin.ignore(cin.rdbuf()->in_avail());
	getline(cin, someFlowers[numOfFlowers].name);
	cout << "Введите цену: ";
	someFlowers[numOfFlowers].price = inputInt(0, 38000);

	numOfFlowers++;
	delete[] flower;

	cout << "Цветок добавлен" << endl;
	system("pause");

	menu(someFlowers, numOfFlowers);
}

void print(flowers* flower, int numOfFlowers) {
	clear();
	cout << "\t" << "Номер" << "\t";
	cout << "\t" << "Название" << "\t";
	cout << "\t" << "Цена" << "\t";
	cout << endl;
	for (int i = 0; i < numOfFlowers; i++) {
		cout << "\t" << i + 1 << "\t";
		cout << "\t" << flower[i].name << "\t";
		cout << "\t" << flower[i].price << "\t";
		cout << endl;
	}
	cout << endl;
	system("pause");
	menu(flower, numOfFlowers);
}

void printForDelete(flowers* flower, int numOfFlowers) {
	clear();
	cout << "\t" << "Номер" << "\t";
	cout << "\t" << "Название" << "\t";
	cout << "\t" << "Цена" << "\t";
	cout << endl;
	for (int i = 0; i < numOfFlowers; i++) {
		cout << "\t" << i + 1 << "\t";
		cout << "\t" << flower[i].name << "\t";
		cout << "\t" << flower[i].price << "\t";
		cout << endl;
	}
	cout << endl;
}

void calculation(flowers* flower, int numOfFlowers) {
	clear();
	cout << "*** Цветок с минимальной ценой ***" << endl;
	int minPointer = 0;
	int minPrice = flower[0].price;
	for (int i = 0; i < numOfFlowers; i++) {
		if (flower[i].price < minPrice) {
			minPointer = i;
		}
	}
	cout << flower[minPointer].name << endl;
	cout << flower[minPointer].price << endl;
	system("pause");
	menu(flower, numOfFlowers);
}

void del(flowers* flower, int numOfFlowers) {
	clear();
	printForDelete(flower, numOfFlowers);
	flowers *someFlower = new flowers[numOfFlowers - 1];
	int delPointer;
	cout << "Введите номер удаляемого элемента: ";
	delPointer = inputInt(1, numOfFlowers);
	int j = 0;
	for (int i = 0; i < numOfFlowers - 1;i++) {
		if (i == delPointer - 1) {
			j++;
			someFlower[i] = flower[j];
			j++;
		}
		else {
			someFlower[i] = flower[j];
			j++;
		}
	}
	delete[] flower;
	cout << "Элемент " << delPointer << " удален" << endl;
	system("pause");
	menu(someFlower, numOfFlowers - 1);
}

void save(flowers* flower, int numOfFlowers) {
	clear();
	fstream file;
	file.open(path, ios::out);
	for (int i = 0; i < numOfFlowers; i++) {
		if (i == numOfFlowers - 1) {
			file << flower[i].name << endl;
			file << flower[i].price;
		}
		else {
			file << flower[i].name << endl;
			file << flower[i].price << endl;
		}
	}
	cout << "*** Данные сохранились ***" << endl;
	system("pause");
	file.close();
	menu(flower, numOfFlowers);
}

int inputInt(int min, int max)
{
	int N;
	for (;;) {
		//std::cout << " (целое от " << min << " до " << max << "): " << std::flush;
		if ((std::cin >> N).good() && (min <= N) && (N <= max)) return N;
		if (std::cin.fail()) {
			std::cin.clear();
			std::cout << "Неверный ввод, повторите.\n";
		}
		else {
			std::cout << "Число вне допустимого диапазона значений. Повторите ввод.\n";
		}
		std::cin.ignore(100, '\n');
	}
}

void clear() {
	COORD topLeft = { 0, 0 };
	HANDLE console = GetStdHandle(STD_OUTPUT_HANDLE);
	CONSOLE_SCREEN_BUFFER_INFO screen;
	DWORD written;

	GetConsoleScreenBufferInfo(console, &screen);
	FillConsoleOutputCharacterA(
		console, ' ', screen.dwSize.X * screen.dwSize.Y, topLeft, &written
	);
	FillConsoleOutputAttribute(
		console, FOREGROUND_GREEN | FOREGROUND_RED | FOREGROUND_BLUE,
		screen.dwSize.X * screen.dwSize.Y, topLeft, &written
	);
	SetConsoleCursorPosition(console, topLeft);
}
