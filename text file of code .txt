 /*  Project #1  
  Management system for a cafe
  BY محمد مجدي علي ابوالنصر */
#include <iostream>
#include <string.h>
using namespace std;
struct client
{
    int id;
    string time;
    string name;
};
int counter = 0;
int big_counter = -1;
//int start = 0;
client array_of_clients[101];
void add_new_client();
void client_update();
void client_Delete();
void show_clients();
int main()
{
    while (1)
    {
        cout << "\n\t"
             << "Welcome to the management system for a cafe\n"
             << endl;
        cout << "1) Add new client.\n"
             << endl;
        cout << "2) Update client.\n"
             << endl;
        cout << "3) Delete client.\n"
             << endl;
        cout << "4) Show all clients attended the cafe.\n"
             << endl;
        cout << "5) Please chose one from above choices: ....\n"
             << endl;
        int choice;
        cin >> choice;

        if (choice == 1)
        {
            add_new_client();
        }
        else if (choice == 2)
        {
            client_update();
        }
        else if (choice == 3)
        {
            client_Delete();
        }
        else if (choice == 4)
        {
            show_clients();
        }
        else
        {
            cout << "\n #\n Error \n # Please chose one from above choices only! \n ";
        }
    }
}

// function to add new clients
void add_new_client()
{
    int choise;
    int idv;

    for (int i = counter; i < 101; i++)
    {
        for (int j = 0; j <= i; j++)
        {
            if (i == 0)
            {
                cout << "\n \t \t Welcome, user \n"
                     << endl;
                cout << "Please enter the id of the client entered the cafe except 0 :  ";
                cin >> array_of_clients[i].id;
                cout << "Please enter the time the client entered the cafe:  ";
                cin >> array_of_clients[i].time;
                cout << "Please enter the client’s name:  ";
                cin >> array_of_clients[i].name;
                counter += 1;
                big_counter += 1;
                break;
            }
            else
            {
                cout << "\n \t \t Welcome, user \n"
                     << endl;
                cout << "Please enter the id of the client entered the cafe:  ";
                cin >> idv;
                // validation for id
                int id_flag = 0;
                for (int k = 0; k <= i; k++)
                {
                    if (idv == array_of_clients[k].id)
                    {
                        cout << "Error there was a client with this id\n"
                             << endl;
                        id_flag = 1;
                        j = 0;
                        break;
                    }
                }
                if (id_flag == 0)
                {
                    /* code */
                    array_of_clients[i].id = idv;
                    cout << "Please enter the time the client entered the cafe:  ";
                    cin >> array_of_clients[i].time;
                    cout << "Please enter the client’s name:  ";
                    cin >> array_of_clients[i].name;
                    counter += 1;
                    big_counter += 1;
                    break;
                }
            }
        }
        cout << "To add other client, press 1 else to exit press 0." << endl;
        cin >> choise;
        if (choise == 1)
        {
            cout << "Your choose: " << 1 << endl;
        }
        else
        {
            cout << "Your choose: " << 0 << endl;
            break;
        }
        // validation for no. of clients
        if (i >= 100)
        {
            cout << "Error you exceeded the maximum number of clients. " << endl;
            break;
        }
    }
}
// function to update clients
void client_update()
{
    int i, j, choice;
    int flag = 0;
    for (i = 0; i < 101; i++)
    {
        int ID;
        cout << "\n \t \t Welcome, user \n"
             << endl;
        cout << "Please enter the id of the client to update:  ";
        cin >> ID;
        // validation for id
        for (j = 0; j < 100; j++)
        {
            if (ID == array_of_clients[j].id)
            {
                flag = 1;
                break;
            }
        }
        if (flag == 0)
        {
            cout << "Error there is no client with this id" << endl;
            i = i - 1;
            continue;
        }

        cout << "Please enter the new time of the client:  ";
        cin >> array_of_clients[j].time;
        cout << "Please enter the new name of the client :  ";
        cin >> array_of_clients[j].name;

        cout << "To update other client, press 1 else to exit press 0." << endl;
        cin >> choice;
        if (choice == 1)
        {
            cout << "Your choose: " << 1 << endl;
        }
        else
        {
            cout << "Your choose: " << 0 << endl;
            break;
        }
    }
}
// function to delete clients
void client_Delete()
{
    int i, j, choice;
    for (int i = 0; i < counter; i++)
    {
        int ID;
        cout << "\n \t \t Welcome, user \n"
             << endl;
        cout << "Please enter the id of the client to delete:  ";
        cin >> ID;
        // validation for id
        int flag = 0;
        for (j = 0; j < counter; j++)
        {
            if (array_of_clients[j].id == ID)
            {
                flag = 1;
                break;
            }
        }

        if (flag == 0)
        {
            cout << "Error there is no client with this id" << endl;
            i = i - 1;
            continue;
        }
        array_of_clients[j].id = 0;
        array_of_clients[j].name = '\0';
        array_of_clients[j].time = '\0';

        /* big_counter -= 1; */
        cout << "Deleted successfully " << endl;
        cout << "To delete other client, press 1 else to exit press 0." << endl;
        cin >> choice;
        if (choice == 1)
        {
            cout << "Your choose: " << 1 << endl;
        }
        else
        {
            cout << "Your choose: " << 0 << endl;
            break;
        }
    }
}
// function to Show all clients attended the cafe.
void show_clients()
{
    if (counter < 0)
    {
        cout << "there is no clients ";
    }
    else
    {
        for (int i = 0; i <= counter; i++)
        {
            if (array_of_clients[i].id == 0 || (array_of_clients[i].name == "\0" && array_of_clients[i].time == "\0"))
            {

                continue;
            }
            else
                cout << i + 1 << ")"
                     << "At  " << array_of_clients[i].time << "  " << array_of_clients[i].name << "  visited the cafe." << endl;
        }
    }
}
