#include <iostream>
#include <fstream>
#include <sstream>
#include <string>

int main() {
    std::string filename;
    std::cout << "Enter the file name: ";
    std::getline(std::cin, filename);

    std::ifstream file(filename);
    if (!file.is_open()) {
        std::cerr << "Could not open file: " << filename << std::endl;
        return 1;
    }

    int wordCount = 0;
    std::string line;

    while (std::getline(file, line)) {
        std::istringstream stream(line);
        std::string word;

        while (stream >> word) {
            wordCount++;
        }
    }

    file.close();

    std::cout << "Total word count: " << wordCount << std::endl;

    return 0;
}
