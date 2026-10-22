# factorio-c-language-calculator
calculator for Gears, iron Plates and iron Ores 


#include <stdio.h>

typedef enum{
    YES = 1, NO = 0
}Answer;

int main(void){

    int chest = 0;
    int ovens = 0;
    int assemblers = 0;
    Answer again = YES; // 1 - YES / 0 - NO


    
    do{
        int ironOre = 0;
        int ironPlate = 0;
        int factoryTime = 0;

        printf("how many iron ores do you have?: ");
        scanf("%d", &ironOre);

        printf("how many ovens do you have?: ");
        scanf("%d", &ovens);

        printf("how many seconds does the factory work?: ");
        scanf("%d", &factoryTime);

        printf("\n");

        int possibleIronPlates = (int)(ovens * factoryTime / 3.2); // calculating POSSIBLE iron plates
        ironPlate = possibleIronPlates < ironOre ? possibleIronPlates : ironOre; // calculating REAL AMOUNT depending on the iron ores we have from the question above &ironOre
        printf("iron plates: %d\n", ironPlate);

        printf("\n");

        int gearsAssemblyTime = 0;

        printf("how many assemblers do you have?: ");
        scanf("%d", &assemblers);
        
        printf("how long does assemblers work (seconds)?: ");
        scanf("%d", &gearsAssemblyTime);

        int gearsAssemblyByPlates = ironPlate / 2; // possible Gears by iron Plates (int ironPlates)
        int gearsAssemblyByTime = (int)(assemblers * gearsAssemblyTime / 0.5); // possible Gears by assembly Time (we receive Time from user &gearsAssemblyTime) above
        int gears = gearsAssemblyByTime < gearsAssemblyByPlates ? gearsAssemblyByTime : gearsAssemblyByPlates;

        //adding the rest to the Chest for future (int chest)
        int leftover = ironPlate - gears * 2;
        chest += leftover;

        printf("- from the %d of iron Plates, you can receive %d Gears for %d seconds (assembly time)\n", ironPlate, gears, gearsAssemblyTime);
        printf("the leftovers are: %d plates\n", leftover);
        printf("there are total of %d plates in the chest\n", chest); //the number increses from each cycle

        printf("\n--------\n");
        printf("would you like to do one more calculation? (1 for YES, 0 for NO): ");
        scanf("%d", &again);
    }while(again == YES);

    printf("\n");
    printf("have a good day, God bless you!\n");

    return 0;
}
