#include <iostream>
#include <locale.h>
#include <cstdlib>
using namespace std;

enum Num_of_commands {
    INPUT = 1,
    PRINT,
    SEARCH,
    EXIT = 0
};

enum {
    SIZE = 1,
    NAME_SIZE = 50,
    SUBJ_SIZE = 50,
    MARK_SIZE = 1
};

struct student {
    char name[NAME_SIZE]{ "No name" };
    int group{};
    struct {
       char subj1[SUBJ_SIZE]{ "No name" };
       int mark1{};
       char subj2[SUBJ_SIZE]{ "No name" };
       int mark2{};
       char subj3[SUBJ_SIZE]{ "No name" };
       int mark3{};
    } discipline{};

};

int main(int argc, char* argv[]) {
    
    system("chcp 1251");
    setlocale(LC_ALL, "Russian");
  
    student group[SIZE];
    int command{ -1 }, num_of_student{};

    do {
        cout << "\n1 - ввести данные группы студентов\n";
        cout << "2 - распечатать группу студентов\n";
        cout << "3 - вывести список студентов, получивших 2 по двум предметам\n";
        cout << "0 - выход из меню\n";
        cin >> command;
        switch (command) {
        case INPUT:
            cout << "Выбрана команда INPUT\n";
            for (int i{}; i < SIZE; i++) {
                cout << "\nВведите данные студента №" << i + 1;
                cout << "\nВведите ФИО студента: ";
                cin.ignore();
                cin.getline(group[i].name, NAME_SIZE);
                cout << "Введите группу студента: ";
                cin >> group[i].group;
                cout << "Введите предмет 1: ";
                cin.ignore();
                cin.getline(group[i].discipline.subj1, SUBJ_SIZE);
                cout << "Введите оценку по предмету 1: ";
                cin >> group[i].discipline.mark1;
                cout << "Введите предмет 2: ";
                cin.ignore();
                cin.getline(group[i].discipline.subj2, SUBJ_SIZE);
                cout << "Введите оценку по предмету 2: ";
                cin >> group[i].discipline.mark2;
                cout << "Введите предмет 3: ";
                cin.ignore();
                cin.getline(group[i].discipline.subj3, SUBJ_SIZE);
                cout << "Введите оценку по предмету 3: ";
                cin >> group[i].discipline.mark3;
            }
            break;
        case PRINT:
            cout << "Выбрана команда PRINT\n";
            for (int i = 0; i < SIZE; i++) {
                cout << "Данные студента №" << i + 1;
                cout << "\n\tФИО студента: " << group[i].name << "\n";
                cout << "\tГруппа студента: " << group[i].group << "\n";
                cout << "\n\tПредмет 1: " << group[i].discipline.subj1;
                cout << "\tОценка по предмету 1: " << group[i].discipline.mark1; "\n";
                cout << "\n\tПредмет 2: " << group[i].discipline.subj2;
                cout << "\tОценка по предмету 2: " << group[i].discipline.mark2; "\n";
                cout << "\n\tПредмет 3: " << group[i].discipline.subj3;
                cout << "\tОценка по предмету 3: " << group[i].discipline.mark3; "\n";
            }
            break;
        case SEARCH:
            cout << "Выбрана команда SEARCH\n";
            for (int i = 0; i < SIZE; i++)
            {
                if ((group[i].discipline.mark1 == 2 && group[i].discipline.mark2 == 2) || (group[i].discipline.mark1 == 2 && group[i].discipline.mark3 == 2) || (group[i].discipline.mark3 == 2 && group[i].discipline.mark2 == 2)) {
                    cout << "ФИО: " << group[num_of_student].name << " Группа: " << group[num_of_student].group << "\n";
                }
            }
                break;
        case EXIT:
            cout << "Выбрана команда EXIT\n";
            break;
        default:
            cout << "Выбрана неверная команда. Попробуйте ещё раз.";
            }
        } while (command);

        return 0;
    }
