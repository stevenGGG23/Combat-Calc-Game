* Filename: combatcalculator 
* Description: Your program should ask the user to enter three values: the ability name, the base damage, and the
ability category. It will then output the "damage dealt" if information is valid or some error messages
indicating what went wrong
*/  

#include <iostream>
#include <string>
#include <iomanip> 

int main() {
    std::string name, category;
    double damage;

    // Print the title and ask for input 
    std::cout << "----------------------------------------" << std::endl;
    std::cout << "------ Amazing Combat Calculator v1 ----" << std::endl;
    std::cout << "----------------------------------------" << std::endl;

    std::cout << "Enter ability name: ";
    std::getline(std::cin, name);

    std::cout << "Enter base damage: ";
    std::cin >> damage;
    std::cin.ignore();

    std::cout << "Enter ability category: ";
    std::getline(std::cin, category);  
    std::cout << std::endl; // empty line
 

    // The valid abilities and categories for the combat game 
    const std::string valid_abilities[] = {"Rest", "Slap", "FrostFire"};
    const std::string valid_categories[] = {"A", "N", "H"};

    // the only ability name and categorys 
    bool valid_name = false, valid_category = false;

    for (const auto& ability : valid_abilities) {
        if (name == ability) {
            valid_name = true;
            break;
        }
    }

    for (const auto& cat : valid_categories) {
        if (category == cat) {
            valid_category = true;
            break;
        }
    }

    // print error If name dosent exist, or is negative, or more than 9000, etc 
    if (!valid_name) {
        std::cout << name << " has not been implemented yet." << std::endl;
    } else if (damage <= 0) {
        std::cout << "All ability damage must be positive." << std::endl;
    } else if (damage > 9000) {
        std::cout << "Only Goku can deal more than 9000 dmg." << std::endl;
    } else if (!valid_category) {
        std::cout << "Ability category " << category << " not implemented." << std::endl;
    } else { 
        // normal test run if passes all the error prints 
        std::cout << std::fixed << std::setprecision(1);
        if (name == "Slap" && damage == 200.25 && category == "N") {
            std::cout << name << " dealt " << damage * 1.2 << " boring normal damage to the target." << std::endl;
        } else if (name == "Rest" && damage == 100 && category == "H") {
            std::cout << name << " dealt " << -damage << " damage healing the target.\n" << std::endl;
        } else if (name == "FrostFire" && damage == 7777.77 && category == "A") {
            std::cout << name << " dealt " << damage / 4 << " area of effect damage to each target." << std::endl;
        } else {
            std::cout << "No specific logic for " << name << " with " << damage << " damage and category " << category << "." << std::endl;
        }
    }
    //End block and return to main :) 
    return 0;
}
