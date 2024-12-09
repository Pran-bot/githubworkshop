# githubworkshop
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

// Constants
#define MAX_DISEASES 100
#define MAX_SYMPTOMS 3
#define MAX_USERS 50

// Structures
typedef struct {
    char name[50];
    char symptoms[MAX_SYMPTOMS][50];
    char prevention[200];
    char severity[10]; // "normal" or "risky"
    char remedy[200];  // Homemade remedy or advice
} Disease;



// Global variables
Disease diseases[MAX_DISEASES];
int diseaseCount = 0;

// Function declarations
void displayMenu();
void checkTemperature();
void searchBySymptoms();
void viewAllDiseases();
void cureDisease();
void storedDiseases();
void loadData();
void saveData();

int main() {
    int choice;

    // stored diseases
    storedDiseases();


    while (1) {
        displayMenu();
        printf("\nEnter your choice: ");
        scanf("%d", &choice);
        getchar(); // Clear input buffer

        switch (choice) {

            case 1:
                checkTemperature();
                break;
            case 2:
                searchBySymptoms();
                break;
            case 3:
                viewAllDiseases();
                break;
            case 4:
                cureDisease();
                break;
            case 5:
                printf("Exiting the program. Goodbye!\n");
                exit(0);
            default:
                printf("Invalid choice! Please try again.\n");
        }
    }

    return 0;
}

// Function to display the menu
void displayMenu() {
    printf("\n Welcome to our disease management system.......\n");

    printf("\n<<<<<<< Disease Management System >>>>>>>\n");
    printf("1. Check Your Body Temperature\n");
    printf("2. Search for diseases by symptoms\n");
    printf("3. View all diseases\n");
    printf("4. Cure a disease\n");
    printf("5. Exit\n");
}

// Function to initialize a list of diseases
void storedDiseases() {
    // Example diseases
    // Disease 1: Common Cold
    strcpy(diseases[0].name, "Common Cold");
    strcpy(diseases[0].symptoms[0], "cough");
    strcpy(diseases[0].symptoms[1], "runny nose");
    strcpy(diseases[0].symptoms[2], "sore throat");
    strcpy(diseases[0].symptoms[3], "congestion");
    strcpy(diseases[0].symptoms[4], "sneezing");
    strcpy(diseases[0].prevention, "Stay hydrated, avoid close contact with infected people.");
    strcpy(diseases[0].severity, "normal");
    strcpy(diseases[0].remedy, "Drink warm ginger tea, rest, and inhale steam.");

    // Disease 2: Dengue
    strcpy(diseases[1].name, "Dengue");
    strcpy(diseases[1].symptoms[0], "high fever");
    strcpy(diseases[1].symptoms[1], "headache");
    strcpy(diseases[1].symptoms[2], "joint pain");
    strcpy(diseases[1].symptoms[3], "rash");
    strcpy(diseases[1].symptoms[4], "muscle pain");
    strcpy(diseases[1].prevention, "Use mosquito repellents, wear long sleeves, and avoid standing water.");
    strcpy(diseases[1].severity, "risky");
    strcpy(diseases[1].remedy, "Consult a doctor immediately.");

    // Disease 3: Malaria
    strcpy(diseases[2].name, "Malaria");
    strcpy(diseases[2].symptoms[0], "fever");
    strcpy(diseases[2].symptoms[1], "chills");
    strcpy(diseases[2].symptoms[2], "sweating");
    strcpy(diseases[2].symptoms[3], "headache");
    strcpy(diseases[2].symptoms[4], "fatigue");
    strcpy(diseases[2].prevention, "Use mosquito nets, avoid stagnant water, and take antimalarial medications.");
    strcpy(diseases[2].severity, "risky");
    strcpy(diseases[2].remedy, "Consult a doctor immediately for proper treatment.");

    // Disease 4: Acidity
    strcpy(diseases[3].name, "Acidity");
    strcpy(diseases[3].symptoms[0], "heartburn");
    strcpy(diseases[3].symptoms[1], "stomach pain");
    strcpy(diseases[3].symptoms[2], "nausea");
    strcpy(diseases[3].symptoms[3], "bloating");
    strcpy(diseases[3].symptoms[4], "belching");
    strcpy(diseases[3].prevention, "Avoid spicy foods, eat smaller meals, and manage stress.");
    strcpy(diseases[3].severity, "normal");
    strcpy(diseases[3].remedy, "Drink cold milk or consume bananas.");

    // Disease 5: Asthma
    strcpy(diseases[4].name, "Asthma");
    strcpy(diseases[4].symptoms[0], "shortness of breath");
    strcpy(diseases[4].symptoms[1], "wheezing");
    strcpy(diseases[4].symptoms[2], "chest tightness");
    strcpy(diseases[4].symptoms[3], "coughing");
    strcpy(diseases[4].symptoms[4], "difficulty breathing after exercise");
    strcpy(diseases[4].prevention, "Avoid allergens, smoke, and use prescribed inhalers.");
    strcpy(diseases[4].severity, "risky");
    strcpy(diseases[4].remedy, "Consult a doctor and use an inhaler as prescribed.");

    // Disease 6: Food Poisoning
    strcpy(diseases[5].name, "Food Poisoning");
    strcpy(diseases[5].symptoms[0], "nausea");
    strcpy(diseases[5].symptoms[1], "vomiting");
    strcpy(diseases[5].symptoms[2], "diarrhea");
    strcpy(diseases[5].symptoms[3], "abdominal pain");
    strcpy(diseases[5].symptoms[4], "fever");
    strcpy(diseases[5].prevention, "Eat freshly prepared food, wash hands frequently.");
    strcpy(diseases[5].severity, "normal");
    strcpy(diseases[5].remedy, "Stay hydrated and take oral rehydration salts.");

    // Disease 7: Typhoid
    strcpy(diseases[6].name, "Typhoid");
    strcpy(diseases[6].symptoms[0], "high fever");
    strcpy(diseases[6].symptoms[1], "abdominal pain");
    strcpy(diseases[6].symptoms[2], "weakness");
    strcpy(diseases[6].symptoms[3], "rash");
    strcpy(diseases[6].symptoms[4], "constipation");
    strcpy(diseases[6].prevention, "Drink clean water and avoid street food.");
    strcpy(diseases[6].severity, "risky");
    strcpy(diseases[6].remedy, "Consult a doctor for proper treatment.");

    // Disease 8: Anemia
    strcpy(diseases[7].name, "Anemia");
    strcpy(diseases[7].symptoms[0], "fatigue");
    strcpy(diseases[7].symptoms[1], "pale skin");
    strcpy(diseases[7].symptoms[2], "shortness of breath");
    strcpy(diseases[7].symptoms[3], "dizziness");
    strcpy(diseases[7].symptoms[4], "headaches");
    strcpy(diseases[7].prevention, "Eat iron-rich foods like spinach, red meat, and lentils.");
    strcpy(diseases[7].severity, "normal");
    strcpy(diseases[7].remedy, "Consume iron-rich foods or take iron supplements as advised by a doctor.");

    // Disease 9: Diabetes
    strcpy(diseases[8].name, "Diabetes");
    strcpy(diseases[8].symptoms[0], "frequent urination");
    strcpy(diseases[8].symptoms[1], "excessive thirst");
    strcpy(diseases[8].symptoms[2], "fatigue");
    strcpy(diseases[8].symptoms[3], "blurred vision");
    strcpy(diseases[8].symptoms[4], "unexplained weight loss");
    strcpy(diseases[8].prevention, "Maintain a balanced diet, exercise regularly, and manage stress.");
    strcpy(diseases[8].severity, "risky");
    strcpy(diseases[8].remedy, "Consult a doctor for proper medication and monitoring.");

    // Disease 10: Skin Allergy
    strcpy(diseases[9].name, "Skin Allergy");
    strcpy(diseases[9].symptoms[0], "itchy skin");
    strcpy(diseases[9].symptoms[1], "rash");
    strcpy(diseases[9].symptoms[2], "redness");
    strcpy(diseases[9].symptoms[3], "swelling");
    strcpy(diseases[9].symptoms[4], "dryness");
    strcpy(diseases[9].prevention, "Avoid allergens and use hypoallergenic products.");
    strcpy(diseases[9].severity, "normal");
    strcpy(diseases[9].remedy, "Apply calamine lotion or aloe vera gel for relief.");

    // Disease 11: Migraine
    strcpy(diseases[10].name, "Migraine");
    strcpy(diseases[10].symptoms[0], "severe headache");
    strcpy(diseases[10].symptoms[1], "nausea");
    strcpy(diseases[10].symptoms[2], "sensitivity to light");
    strcpy(diseases[10].symptoms[3], "vomiting");
    strcpy(diseases[10].symptoms[4], "blurred vision");
    strcpy(diseases[10].prevention, "Avoid triggers like stress, caffeine, and loud noises.");
    strcpy(diseases[10].severity, "normal");
    strcpy(diseases[10].remedy, "Rest in a dark room and apply a cold compress.");

    // Disease 12: Chickenpox
    strcpy(diseases[11].name, "Chickenpox");
    strcpy(diseases[11].symptoms[0], "fever");
    strcpy(diseases[11].symptoms[1], "itchy rash");
    strcpy(diseases[11].symptoms[2], "blisters");
    strcpy(diseases[11].symptoms[3], "fatigue");
    strcpy(diseases[11].symptoms[4], "loss of appetite");
    strcpy(diseases[11].prevention, "Vaccination and avoiding contact with infected people.");
    strcpy(diseases[11].severity, "normal");
    strcpy(diseases[11].remedy, "Apply calamine lotion to reduce itching and rest.");

    // Disease 13: Tuberculosis (TB)
    strcpy(diseases[12].name, "Tuberculosis");
    strcpy(diseases[12].symptoms[0], "coughing up blood");
    strcpy(diseases[12].symptoms[1], "fever");
    strcpy(diseases[12].symptoms[2], "night sweats");
    strcpy(diseases[12].symptoms[3], "weight loss");
    strcpy(diseases[12].symptoms[4], "fatigue");
    strcpy(diseases[12].prevention, "Avoid close contact with infected people, complete TB treatment.");
    strcpy(diseases[12].severity, "risky");
    strcpy(diseases[12].remedy, "Consult a doctor for antibiotics and a full course of treatment.");

    // Disease 14: Pneumonia
    strcpy(diseases[13].name, "Pneumonia");
    strcpy(diseases[13].symptoms[0], "coughing");
    strcpy(diseases[13].symptoms[1], "chest pain");
    strcpy(diseases[13].symptoms[2], "fever");
    strcpy(diseases[13].symptoms[3], "shortness of breath");
    strcpy(diseases[13].symptoms[4], "fatigue");
    strcpy(diseases[13].prevention, "Vaccination and avoiding close contact with infected people.");
    strcpy(diseases[13].severity, "risky");
    strcpy(diseases[13].remedy, "Consult a doctor for antibiotics and proper treatment.");

    // Disease 15: Hepatitis A
    strcpy(diseases[14].name, "Hepatitis A");
    strcpy(diseases[14].symptoms[0], "fatigue");
    strcpy(diseases[14].symptoms[1], "nausea");
    strcpy(diseases[14].symptoms[2], "abdominal pain");
    strcpy(diseases[14].symptoms[3], "loss of appetite");
    strcpy(diseases[14].symptoms[4], "yellowing of skin");
    strcpy(diseases[14].prevention, "Vaccination, avoid drinking contaminated water.");
    strcpy(diseases[14].severity, "risky");
    strcpy(diseases[14].remedy, "Consult a doctor and follow a balanced diet.");

    // Disease 16: Hepatitis B
    strcpy(diseases[15].name, "Hepatitis B");
    strcpy(diseases[15].symptoms[0], "fatigue");
    strcpy(diseases[15].symptoms[1], "dark urine");
    strcpy(diseases[15].symptoms[2], "abdominal pain");
    strcpy(diseases[15].symptoms[3], "nausea");
    strcpy(diseases[15].symptoms[4], "yellowing of skin");
    strcpy(diseases[15].prevention, "Vaccination and avoiding contaminated needles.");
    strcpy(diseases[15].severity, "risky");
    strcpy(diseases[15].remedy, "Consult a doctor for antivirals and follow their instructions.");

    // Disease 17: Hepatitis C
    strcpy(diseases[16].name, "Hepatitis C");
    strcpy(diseases[16].symptoms[0], "fatigue");
    strcpy(diseases[16].symptoms[1], "dark urine");
    strcpy(diseases[16].symptoms[2], "abdominal pain");
    strcpy(diseases[16].symptoms[3], "yellowing of skin");
    strcpy(diseases[16].symptoms[4], "loss of appetite");
    strcpy(diseases[16].prevention, "Avoid sharing needles, practice safe sex.");
    strcpy(diseases[16].severity, "risky");
    strcpy(diseases[16].remedy, "Consult a doctor for antivirals and blood tests.");

    // Disease 18: Influenza (Flu)
    strcpy(diseases[17].name, "Influenza");
    strcpy(diseases[17].symptoms[0], "fever");
    strcpy(diseases[17].symptoms[1], "cough");
    strcpy(diseases[17].symptoms[2], "body aches");
    strcpy(diseases[17].symptoms[3], "fatigue");
    strcpy(diseases[17].symptoms[4], "sore throat");
    strcpy(diseases[17].prevention, "Get vaccinated and avoid close contact with infected individuals.");
    strcpy(diseases[17].severity, "normal");
    strcpy(diseases[17].remedy, "Rest, drink fluids, and take over-the-counter medications.");

    // Disease 19: Scarlet Fever
    strcpy(diseases[18].name, "Scarlet Fever");
    strcpy(diseases[18].symptoms[0], "high fever");
    strcpy(diseases[18].symptoms[1], "rash");
    strcpy(diseases[18].symptoms[2], "sore throat");
    strcpy(diseases[18].symptoms[3], "red tongue");
    strcpy(diseases[18].symptoms[4], "chills");
    strcpy(diseases[18].prevention, "Good hygiene and avoid contact with infected people.");
    strcpy(diseases[18].severity, "risky");
    strcpy(diseases[18].remedy, "Consult a doctor for antibiotics.");

    // Disease 20: Pneumonia
    strcpy(diseases[19].name, "Pneumonia");
    strcpy(diseases[19].symptoms[0], "coughing");
    strcpy(diseases[19].symptoms[1], "chest pain");
    strcpy(diseases[19].symptoms[2], "fever");
    strcpy(diseases[19].symptoms[3], "shortness of breath");
    strcpy(diseases[19].symptoms[4], "fatigue");
    strcpy(diseases[19].prevention, "Vaccination and avoiding close contact with infected people.");
    strcpy(diseases[19].severity, "risky");
    strcpy(diseases[19].remedy, "Consult a doctor for antibiotics and proper treatment.");

    // Disease 21: Jaundice
    strcpy(diseases[20].name, "Jaundice");
    strcpy(diseases[20].symptoms[0], "yellowing of skin");
    strcpy(diseases[20].symptoms[1], "dark urine");
    strcpy(diseases[20].symptoms[2], "nausea");
    strcpy(diseases[20].symptoms[3], "loss of appetite");
    strcpy(diseases[20].symptoms[4], "fatigue");
    strcpy(diseases[20].prevention, "Avoid alcohol, ensure proper hygiene.");
    strcpy(diseases[20].severity, "risky");
    strcpy(diseases[20].remedy, "Consult a doctor for liver function tests and treatment.");

    // Disease 22: Chickenpox
    strcpy(diseases[21].name, "Chickenpox");
    strcpy(diseases[21].symptoms[0], "fever");
    strcpy(diseases[21].symptoms[1], "itchy rash");
    strcpy(diseases[21].symptoms[2], "blisters");
    strcpy(diseases[21].symptoms[3], "fatigue");
    strcpy(diseases[21].symptoms[4], "loss of appetite");
    strcpy(diseases[21].prevention, "Vaccination and avoiding contact with infected people.");
    strcpy(diseases[21].severity, "normal");
    strcpy(diseases[21].remedy, "Apply calamine lotion to reduce itching and rest.");

    // Disease 23: Gallstones
    strcpy(diseases[22].name, "Gallstones");
    strcpy(diseases[22].symptoms[0], "abdominal pain");
    strcpy(diseases[22].symptoms[1], "nausea");
    strcpy(diseases[22].symptoms[2], "vomiting");
    strcpy(diseases[22].symptoms[3], "digestive issues");
    strcpy(diseases[22].symptoms[4], "bloating");
    strcpy(diseases[22].prevention, "Eat a balanced diet with plenty of fiber.");
    strcpy(diseases[22].severity, "risky");
    strcpy(diseases[22].remedy, "Consult a doctor for possible surgery or medications.");

    // Disease 24: Kidney Stones
    strcpy(diseases[23].name, "Kidney Stones");
    strcpy(diseases[23].symptoms[0], "severe back pain");
    strcpy(diseases[23].symptoms[1], "pain during urination");
    strcpy(diseases[23].symptoms[2], "blood in urine");
    strcpy(diseases[23].symptoms[3], "frequent urination");
    strcpy(diseases[23].symptoms[4], "nausea");
    strcpy(diseases[23].prevention, "Stay hydrated and maintain a healthy diet.");
    strcpy(diseases[23].severity, "risky");
    strcpy(diseases[23].remedy, "Consult a doctor for pain relief and treatment.");

    // Disease 25: Appendicitis
    strcpy(diseases[24].name, "Appendicitis");
    strcpy(diseases[24].symptoms[0], "abdominal pain");
    strcpy(diseases[24].symptoms[1], "nausea");
    strcpy(diseases[24].symptoms[2], "fever");
    strcpy(diseases[24].symptoms[3], "loss of appetite");
    strcpy(diseases[24].symptoms[4], "swelling of the abdomen");
    strcpy(diseases[24].prevention, "There is no specific prevention, but avoid infections.");
    strcpy(diseases[24].severity, "risky");
    strcpy(diseases[24].remedy, "Consult a doctor immediately for possible surgery.");

    // Disease 26: Celiac Disease
    strcpy(diseases[25].name, "Celiac Disease");
    strcpy(diseases[25].symptoms[0], "diarrhea");
    strcpy(diseases[25].symptoms[1], "fatigue");
    strcpy(diseases[25].symptoms[2], "abdominal pain");
    strcpy(diseases[25].symptoms[3], "bloating");
    strcpy(diseases[25].symptoms[4], "weight loss");
    strcpy(diseases[25].prevention, "Avoid gluten-containing foods.");
    strcpy(diseases[25].severity, "normal");
    strcpy(diseases[25].remedy, "Follow a strict gluten-free diet.");

    // Disease 27: Asthma
    strcpy(diseases[26].name, "Asthma");
    strcpy(diseases[26].symptoms[0], "shortness of breath");
    strcpy(diseases[26].symptoms[1], "wheezing");
    strcpy(diseases[26].symptoms[2], "coughing");
    strcpy(diseases[26].symptoms[3], "tightness in chest");
    strcpy(diseases[26].symptoms[4], "fatigue");
    strcpy(diseases[26].prevention, "Avoid triggers and use inhalers.");
    strcpy(diseases[26].severity, "normal");
    strcpy(diseases[26].remedy, "Consult a doctor for asthma inhalers and medications.");

    // Disease 28: Migraine
    strcpy(diseases[27].name, "Migraine");
    strcpy(diseases[27].symptoms[0], "severe headache");
    strcpy(diseases[27].symptoms[1], "nausea");
    strcpy(diseases[27].symptoms[2], "sensitivity to light");
    strcpy(diseases[27].symptoms[3], "blurred vision");
    strcpy(diseases[27].symptoms[4], "vomiting");
    strcpy(diseases[27].prevention, "Avoid triggers like stress, lack of sleep, and certain foods.");
    strcpy(diseases[27].severity, "normal");
    strcpy(diseases[27].remedy, "Rest in a dark room, drink water, and take pain relievers.");

    // Disease 29: Chronic Fatigue Syndrome
    strcpy(diseases[28].name, "Chronic Fatigue Syndrome");
    strcpy(diseases[28].symptoms[0], "extreme fatigue");
    strcpy(diseases[28].symptoms[1], "muscle pain");
    strcpy(diseases[28].symptoms[2], "poor memory");
    strcpy(diseases[28].symptoms[3], "sleep disturbance");
    strcpy(diseases[28].symptoms[4], "headache");
    strcpy(diseases[28].prevention, "Healthy lifestyle and stress management.");
    strcpy(diseases[28].severity, "normal");
    strcpy(diseases[28].remedy, "Consult a doctor for treatment and therapy.");

    // Disease 30: Malaria
    strcpy(diseases[29].name, "Malaria");
    strcpy(diseases[29].symptoms[0], "fever");
    strcpy(diseases[29].symptoms[1], "chills");
    strcpy(diseases[29].symptoms[2], "headache");
    strcpy(diseases[29].symptoms[3], "nausea");
    strcpy(diseases[29].symptoms[4], "fatigue");
    strcpy(diseases[29].prevention, "Use mosquito repellents and sleep under nets.");
    strcpy(diseases[29].severity, "risky");
    strcpy(diseases[29].remedy, "Consult a doctor for anti-malarial medications.");

    // Disease 31: Dengue Fever
    strcpy(diseases[30].name, "Dengue Fever");
    strcpy(diseases[30].symptoms[0], "high fever");
    strcpy(diseases[30].symptoms[1], "severe headache");
    strcpy(diseases[30].symptoms[2], "pain behind eyes");
    strcpy(diseases[30].symptoms[3], "rash");
    strcpy(diseases[30].symptoms[4], "muscle and joint pain");
    strcpy(diseases[30].prevention, "Avoid mosquito bites, use repellents.");
    strcpy(diseases[30].severity, "risky");
    strcpy(diseases[30].remedy, "Consult a doctor for proper treatment and hydration.");

    // Disease 32: Stroke
    strcpy(diseases[31].name, "Stroke");
    strcpy(diseases[31].symptoms[0], "sudden numbness or weakness");
    strcpy(diseases[31].symptoms[1], "confusion");
    strcpy(diseases[31].symptoms[2], "difficulty speaking");
    strcpy(diseases[31].symptoms[3], "vision problems");
    strcpy(diseases[31].symptoms[4], "loss of balance");
    strcpy(diseases[31].prevention, "Control blood pressure, avoid smoking.");
    strcpy(diseases[31].severity, "risky");
    strcpy(diseases[31].remedy, "Consult a doctor immediately, as stroke requires urgent care.");

    // Disease 33: Alzheimer's Disease
    strcpy(diseases[32].name, "Alzheimer's Disease");
    strcpy(diseases[32].symptoms[0], "memory loss");
    strcpy(diseases[32].symptoms[1], "difficulty performing familiar tasks");
    strcpy(diseases[32].symptoms[2], "confusion");
    strcpy(diseases[32].symptoms[3], "mood swings");
    strcpy(diseases[32].symptoms[4], "disorientation");
    strcpy(diseases[32].prevention, "Regular mental exercises and physical activity.");
    strcpy(diseases[32].severity, "risky");
    strcpy(diseases[32].remedy, "Consult a doctor for medication and therapy.");

    // Disease 34: Parkinson's Disease
    strcpy(diseases[33].name, "Parkinson's Disease");
    strcpy(diseases[33].symptoms[0], "tremors");
    strcpy(diseases[33].symptoms[1], "stiffness");
    strcpy(diseases[33].symptoms[2], "slowed movement");
    strcpy(diseases[33].symptoms[3], "difficulty balancing");
    strcpy(diseases[33].symptoms[4], "changes in handwriting");
    strcpy(diseases[33].prevention, "Regular physical activity and a balanced diet.");
    strcpy(diseases[33].severity, "risky");
    strcpy(diseases[33].remedy, "Consult a doctor for medication and physical therapy.");

    // Disease 35: Irritable Bowel Syndrome (IBS)
    strcpy(diseases[34].name, "Irritable Bowel Syndrome (IBS)");
    strcpy(diseases[34].symptoms[0], "abdominal pain");
    strcpy(diseases[34].symptoms[1], "bloating");
    strcpy(diseases[34].symptoms[2], "diarrhea");
    strcpy(diseases[34].symptoms[3], "constipation");
    strcpy(diseases[34].symptoms[4], "nausea");
    strcpy(diseases[34].prevention, "Avoid trigger foods and manage stress.");
    strcpy(diseases[34].severity, "normal");
    strcpy(diseases[34].remedy, "Dietary changes, stress management, and over-the-counter medications.");

    // Disease 36: Psoriasis
    strcpy(diseases[35].name, "Psoriasis");
    strcpy(diseases[35].symptoms[0], "itchy skin patches");
    strcpy(diseases[35].symptoms[1], "red, inflamed skin");
    strcpy(diseases[35].symptoms[2], "silvery scales");
    strcpy(diseases[35].symptoms[3], "dry skin cracks");
    strcpy(diseases[35].symptoms[4], "swollen joints");
    strcpy(diseases[35].prevention, "Avoid triggers like stress and smoking.");
    strcpy(diseases[35].severity, "normal");
    strcpy(diseases[35].remedy, "Topical treatments like creams and ointments, phototherapy.");

    // Disease 37: Eczema
    strcpy(diseases[36].name, "Eczema");
    strcpy(diseases[36].symptoms[0], "itchy skin");
    strcpy(diseases[36].symptoms[1], "red patches of skin");
    strcpy(diseases[36].symptoms[2], "dry skin");
    strcpy(diseases[36].symptoms[3], "blisters");
    strcpy(diseases[36].symptoms[4], "cracked skin");
    strcpy(diseases[36].prevention, "Avoid triggers such as allergens and stress.");
    strcpy(diseases[36].severity, "normal");
    strcpy(diseases[36].remedy, "Topical steroids, moisturizing creams, and avoiding triggers.");

    // Disease 38: Bronchitis
    strcpy(diseases[37].name, "Bronchitis");
    strcpy(diseases[37].symptoms[0], "persistent cough");
    strcpy(diseases[37].symptoms[1], "fatigue");
    strcpy(diseases[37].symptoms[2], "shortness of breath");
    strcpy(diseases[37].symptoms[3], "chest discomfort");
    strcpy(diseases[37].symptoms[4], "production of mucus");
    strcpy(diseases[37].prevention, "Avoid smoking, stay away from polluted air.");
    strcpy(diseases[37].severity, "normal");
    strcpy(diseases[37].remedy, "Rest, stay hydrated, and use expectorants.");

    // Disease 39: Conjunctivitis (Pink Eye)
    strcpy(diseases[38].name, "Conjunctivitis (Pink Eye)");
    strcpy(diseases[38].symptoms[0], "redness in the eye");
    strcpy(diseases[38].symptoms[1], "itchiness or irritation");
    strcpy(diseases[38].symptoms[2], "watery eyes");
    strcpy(diseases[38].symptoms[3], "sensitivity to light");
    strcpy(diseases[38].symptoms[4], "swelling of eyelids");
    strcpy(diseases[38].prevention, "Avoid touching eyes with dirty hands, practice good hygiene.");
    strcpy(diseases[38].severity, "normal");
    strcpy(diseases[38].remedy, "Use warm compresses, and consult a doctor if necessary.");

    // Disease 40: Anemia
    strcpy(diseases[39].name, "Anemia");
    strcpy(diseases[39].symptoms[0], "fatigue");
    strcpy(diseases[39].symptoms[1], "weakness");
    strcpy(diseases[39].symptoms[2], "pale skin");
    strcpy(diseases[39].symptoms[3], "shortness of breath");
    strcpy(diseases[39].symptoms[4], "dizziness");
    strcpy(diseases[39].prevention, "Eat iron-rich foods and maintain a balanced diet.");
    strcpy(diseases[39].severity, "normal");
    strcpy(diseases[39].remedy, "Iron supplements and dietary adjustments.");

    diseaseCount = 40;
}



// Function to search diseases by symptoms
void searchBySymptoms() {
    char userSymptoms[MAX_SYMPTOMS][50];
    printf("\nEnter 3 symptoms to search:\n");
    for (int i = 0; i < MAX_SYMPTOMS; i++) {
        printf("Symptom %d: ", i + 1);
        fgets(userSymptoms[i], sizeof(userSymptoms[i]), stdin);
        userSymptoms[i][strcspn(userSymptoms[i], "\n")] = '\0';
    }

    int found = 0;
    printf("\n=== Search Results ===\n");
    for (int i = 0; i < diseaseCount; i++) {
        int matchCount = 0;
        for (int j = 0; j < MAX_SYMPTOMS; j++) {
            for (int k = 0; k < MAX_SYMPTOMS; k++) {
                if (strcasecmp(userSymptoms[j], diseases[i].symptoms[k]) == 0) {
                    matchCount++;
                }
            }
        }
        if (matchCount > 0) {//match is for the ease of user to know the exact disease
            found = 1;
            printf("\nDisease: %s\n", diseases[i].name);
            printf("Prevention: %s\n", diseases[i].prevention);
            printf("Match Score: %d/%d\n", matchCount, MAX_SYMPTOMS);
        }
    }

    if (!found) {
        printf("No matching diseases found!\n");
    }
}

// Function to view all diseases
void viewAllDiseases() {
    printf("\n=== List of Diseases ===\n");
    for (int i = 0; i < diseaseCount; i++) {
        printf("\nDisease: %s\n", diseases[i].name);
        printf("Symptoms: ");
        for (int j = 0; j < MAX_SYMPTOMS; j++) {
            printf("%s", diseases[i].symptoms[j]);
            if (j < MAX_SYMPTOMS - 1) printf(", ");
        }
        printf("\nPrevention: %s\n", diseases[i].prevention);
        printf("Severity: %s\n", diseases[i].severity);
    }
}



// Function to provide a cure for diseases
void cureDisease() {
    char diseaseName[50];
    printf("\nEnter the disease name: ");
    fgets(diseaseName, sizeof(diseaseName), stdin);
    diseaseName[strcspn(diseaseName, "\n")] = '\0';

    int found = 0;
    for (int i = 0; i < diseaseCount; i++) {
        if (strcasecmp(diseases[i].name, diseaseName) == 0) {
            found = 1;
            printf("\n=== Cure for %s ===\n", diseases[i].name);
            if (strcmp(diseases[i].severity, "normal") == 0) {
                printf("Homemade Remedy: %s\n", diseases[i].remedy);
            } else {
                printf("Advice: %s\n", diseases[i].remedy);
            }
            break;
        }
    }

    if (!found) {
        printf("Disease not found in the database.\n");
    }
}
void checkTemperature() {
 float temperature;
    printf("Enter your body temperature in Celsius:");
    scanf("%f",&temperature);
    if(temperature< 35.0 ){
        printf("\n Body temperature is too low.\n");
    }else if( temperature >= 35.0 && temperature <= 37.2 ){
        printf("\n Body temperature is normal.\n");
    }else{
        printf("\n Body temperature is above normal.\n");
    }

}




