#include <iostream>
#include <cstdlib> // For system()

void displayMenu();
void listFiles();
void createDirectory();
void changeDirectory();

int main() {
    int choice;

    do {
        displayMenu();
        std::cout << "Enter the Number: ";
        std::cin >> choice;

        switch (choice) {
            case 1:
                listFiles();
                break;
            case 2:
                createDirectory();
                break;
            case 3:
                changeDirectory();
                break;
            case 4:
                std::cout << "Exiting...\n";
                return 0;
            default:
                std::cout << "Invalid option, please try again.\n";
        }
    } while (choice != 4);

    return 0;
}

void displayMenu() {
    std::cout << "\n\t\t\tMAIN MENU\n\t\t-----------------------\n";
    std::cout << "1. Display List of Files\n";
    std::cout << "2. Create New Directory\n";
    std::cout << "3. Change the Working Directory\n";
    std::cout << "4. Exit\n";
}

void listFiles() {
    std::cout << "Listing files in the current directory:\n";
    system("dir"); // Lists files using the 'dir' command
}

void createDirectory() {
    std::cout << "Enter the Directory name: ";
    std::string dirName;
    std::cin >> dirName;

    std::string command = "md " + dirName;

    if (system(command.c_str()) == 0) {
        std::cout << dirName << " Directory Successfully Created\n";
    } else {
        std::cout << "Failed to create directory " << dirName << "\n";
    }
}

void changeDirectory() {
    std::cout << "\nCurrent Directory:\n";
    system("cd"); // Display current directory

    std::cout << "Enter the directory name to change to: ";
    std::string newDir;
    std::cin >> newDir;

    std::string command = "cd " + newDir;

    if (system(command.c_str()) == 0) {
        std::cout << "Directory changed successfully\n";
    } else {
        std::cout << "Failed to change directory\n";
    }

    std::cout << "Current Directory:\n";
    system("cd"); // Display current directory after change
}
