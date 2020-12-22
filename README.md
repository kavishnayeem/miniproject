# miniproject
#include<stdlib.h>
#include<stdio.h>
#include<string.h>
void display();
void noticeboard();
void studentlogin();
void adminlogin();
void viewprofile(char* );
void editprofile(char* );
void viewmarks(char* );
void uploadmarks();
void editnoticeboard();
void searchstudent();
void viewattendance(char *);
void uploadattendance();
int main()
{
system("clear");
char login;
display();
noticeboard();
while(1){
        printf(" _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _  \n");
        printf("|For STUDENT login press--->'s' |\n");
        printf("|For ADMIN login press----->'a' |\n");
        printf("|To SEARCH a student press->'S' |\n");
        printf("|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|\n\n");
        printf(" ENTER HERE :");
        scanf(" %c",&login);
        if(login=='s'){
                studentlogin();
                break;}
        else if(login=='a'){
                adminlogin();
                break;}
        else if(login=='S'){
                searchstudent();
                break;}
        else
                printf("\nWRONG INPUT ENTER AGAIN\n");
        }
return 0;
}
void studentlogin()
{
        FILE *f;
        char rollnumber[20],password[20],c,r[20];
        int i,j;
        system("clear");
        printf("\n\n\n\t\t\t\t\t\t______ S T U D E N T  L O G I N ______\n");
        for(j=0;j<3;j++){
                printf("\nEnter your roll number in 1602-XX-XXX-XXX format:");
                scanf("%s", rollnumber);
                strcpy(r,rollnumber);
                strcat(r,".txt");
                if(f=fopen(r,"r"))
                        break;
                else
                        printf("\nStudent Profile doesnt exist please enter valid rollnumber\n\n");
        }
        if(j==3)
                main();
        for(i=0;i<3;i++){
                printf("\nEnter password :");
                scanf("%s",password);
                if(strcmp(password,"vasavi"))
                        printf("\nWrong password enter again");
                else{
                        printf("\n\n\n _ _ _ _ _ _ _ _ _ _ _ _ _ _ _\n");
                        printf("|Enter 'm' to VIEW MARKS      |\n");
                        printf("|Enter 'e' to EDIT PROFILE    |\n");
                        printf("|Enter 'v' to VIEW PROFILE    |\n");
                        printf("|Enter 'a' to VIEW ATTENDANCE |\n");
                        printf("|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _|\n");
                        printf("\n ENTER HERE :");
                        scanf(" %c",&c);
                        break;}
        }
        if(c=='v'){
                system("clear");
                viewprofile(rollnumber);}
        else if(c=='e'){
                system("clear");
                editprofile(rollnumber);}
        else if(c=='m'){
                system("clear");
  viewmarks(rollnumber);}
        else if(c=='a'){
                system("clear");
                viewattendance(rollnumber);}
        else{
                printf("Wrong Input");}
}
void adminlogin()
{
        char c;
        int i;
        char password[20];
        char defaultpassword[]="vasaviadmin";
        system("clear");
        printf("\n\n\n\t\t\t\t\t\t\t_______ A D M I N   L O G I N _______\n");
        printf("\nEnter password :");
        scanf("%s",password);
        for(i=0;i<3;i++){
                if(strcmp(defaultpassword,password)){
                        printf("Enter your password again:");
                        scanf("%s",password);}
                else{
                        printf("\n\n\n _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _");
                        printf("\n|Enter e to EDIT NOTICEBOARD      |");
                        printf("\n|Enter m to UPLOAD STUDENTS MARKS |");
                        printf("\n|Enter a to UPLOAD ATTENDANCE     |");
                        printf("\n|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|");
                        printf("\n\nENTER HERE :");
                        scanf(" %c",&c);
                        break;}
        }
        if(c=='e')
                editnoticeboard();
        else if(c=='m')
                uploadmarks();
        else if(c=='a')
                uploadattendance();

}
void display(){
        printf("\t\t\t\t _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _       \n");
        printf("\t\t\t\t|  _        _    _ _ _ _ _    _ _ _ _ _     _ _ _ _ _    _        _    _ _ _ _ _ _    |      \n");
        printf("\t\t\t\t| |+|      |+|  |+|-+-+-|+|  |+|-+-+-|+|   |+|-+-+-|+|  |+|      |+|  |+-+-|+|-+-+|   |      \n");
        printf("\t\t\t\t|  |+|    |+|   |+|_____|+|  |+|_______    |+|_____|+|   |+|    |+|        |+|        |      \n");
        printf("\t\t\t\t|   |+|  |+|    |+|-+-+-|+|  |+|-+-+-|+|   |+|-+-+-|+|    |+|  |+|         |+|        |      \n");
        printf("\t\t\t\t|    |+||+|     |+|     |+|   _ _ _ _|+|   |+|     |+|     |+||+|      _ _ |+|_ _ _   |      \n");
        printf("\t\t\t\t|     |++|      |+|     |+|  |+|-+-+-|+|   |+|     |+|      |++|      |+-+-|+|-+-|+|  |      \n");
        printf("\t\t\t\t|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|      \n");
        printf("\t\t\t\t                  _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _                         \n");
        printf("\t\t\t\t                 |                                                   |                        \n");
        printf("\t\t\t\t                 | C O L L E G E      O F      E N G I N E E R I N G |                        \n");
        printf("\t\t\t\t                 |_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|                        \n\n\n\n\n\n");
}
void viewprofile(char *rollnumber)
{       system("clear");
        char c;
        strcat(rollnumber,".txt");
        FILE *f;
        f=fopen(rollnumber,"r");
        while((c=getc(f))!=EOF)
                putchar(c);
        fclose(f);
        printf("\n _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ ");
        printf("\n|Enter 'm' to RETURN TO MAIN MENU   |");
        printf("\n|Enter 'e' to EXIT                  |");
        printf("\n|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|");
        printf("\n\nENTER HERE :");
        scanf(" %c",&c);
        if(c=='m')
                main();
}
void  editprofile(char *rollnumber)
{
        char view;
        char r[20];
        strcpy(r,rollnumber);
        printf("..........EDITING MODE ON..........");
        char c;
        FILE *f;
        strcat(rollnumber,".txt");
        f=fopen(rollnumber,"w");
        fputs("\t\t\t\t\t\t\tN O T E : press ctrl + d to confirm",f);
 fputs("\n\n\n\t\t\t\t\t\t\t_____ S T U D E N T   P R O F I L E _____\n\n\n",f);
        printf("\nEnter your name:");
        fputs("NAME : ",f);
        while((c=getchar())!=EOF)
                putc(c,f);
        fputs("\n\n\n",f);
        fclose(f);
        f=fopen(rollnumber,"a");
                printf("\nEnter your father name:");
                fputs("FATHER'S NAME : ",f);
                while((c=getchar())!=EOF)
                        putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
        f=fopen(rollnumber,"a");
                printf("\nEnter your  mother name:");
                fputs("MOTHER'S NAME : ",f);
                while((c=getchar())!=EOF)
                        putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
         f=fopen(rollnumber,"a");
                printf("\nEnter your house number");
                fputs("HOUSE NO  : ",f);
                while((c=getchar())!=EOF)
                        putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
         f=fopen(rollnumber,"a");
                printf("\nEnter your area name:");
                fputs("AREA : ",f);
                while((c=getchar())!=EOF)
                        putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
         f=fopen(rollnumber,"a");
                printf("\nEnter your city name:");
                fputs("CITY : ",f);
                while((c=getchar())!=EOF)
                        putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
         f=fopen(rollnumber,"a");
 printf("\nEnter your state name:");
                fputs("STATE : :",f);
                while((c=getchar())!=EOF)
                        putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
        printf("\n _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ \n");
        printf("|Enter 'v' to VIEW PROFILE        |\n");
        printf("|Enter 'm' to RETURN TO MAIN MENU |\n");
        printf("|Enter 'e' to EXIT                |\n");
        printf("|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|\n");
        printf("\nENTER HERE :");
        scanf(" %c",&view);
        if(view=='v')
                viewprofile(r);
        else if(view=='m')
                main();
}
void viewmarks(char *rollnumber)
{
        char c;
        strcat(rollnumber,"m.txt");
        FILE *f;
        f=fopen(rollnumber,"r");
        while((c=getc(f))!=EOF)
                putchar(c);
        fclose(f);
        printf("\n\nEnter m to RETURN TO MAIN MENU||Enter e to EXIT :");
        scanf(" %c",&c);
        if(c=='m')
                main();
}
void noticeboard()
{
        char c;
        FILE *f;
        f=fopen("noticeboard.txt","r");
        printf("================================================================================================\n");
        printf("                                  | N O T I C E   B O A R D |                    \n");
        printf("================================================================================================\n");
        if(f!=NULL){
                while((c=getc(f))!=EOF)
                        putchar(c);
 fclose(f);}
        else
                printf("* * *N O --C O N T E N T* * *\n");
        printf("\n________________________________________________________________________________________________\n\n\n");
}
void editnoticeboard()
{
        char c,a;
        FILE *f;
        printf("\nEnter w to REWRITE NOTICEBOARD|Enter a to APPEND NOTICEBOARD:");
        scanf(" %c",&a);
        if(a=='w'){
                system("clear");
                printf("\t\t\t\t\t\t\tN O T E : press ctrl+d to confirm information\n");
                f=fopen("noticeboard.txt","w");
                printf("\n...........REWRITING MODE ON........\n");
                while((c=getchar())!=EOF)
                        putc(c,f);
                fclose(f);}
        else if(a=='a'){
                system("clear");
                printf("\t\t\t\t\t\t\tT I P: press ctrl+d to confirm information\n");
                printf("\n...........APPENDING MODE ON........\n");
                f=fopen("noticeboard.txt","a");
                while((c=getchar())!=EOF)
                        putc(c,f);
                fclose(f);}
                main();
}
void uploadmarks()
{
        char c,a;
        FILE *f;
        char rollnumber[20];
        while(1){
                printf("\t\t\t\t\t\t\tN O T E : press ctrl+d to confirm\n\n");
                printf("\nEnter rollnumber:");
                scanf("%s",rollnumber);
                strcat(rollnumber,"m.txt");
                f=fopen(rollnumber,"w");
                fputs("\t\t\t\t\t\t\t__________ S T U D E N T   M A R K S __________\n\n\n",f);
                printf("\nEnter the marks of:");
                printf("\nMATHS:");
 fputs("M A T H S : ",f);
                while((c=getchar())!=EOF)
                        putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
                f=fopen(rollnumber,"a");
                printf("\nENGLISH:");
                fputs("E N G L I S H : ",f);
                while((c=getchar())!=EOF)
                        putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
                f=fopen(rollnumber,"a");
                printf("\nPROGRAMMING:");
                fputs("P R O G R A M M I N G : ",f);
                while((c=getchar())!=EOF)
                        putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
                f=fopen(rollnumber,"a");
                printf("\nDATA STRUCTURES:");
                fputs("D A T A  S T R U C T U R E S : ",f);
                while((c=getchar())!=EOF)
                         putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
                f=fopen(rollnumber,"a");
                printf("\nOPEN ELECTIVE:");
                fputs("O P E N  E L E C T I V E : ",f);
                while((c=getchar())!=EOF)
                        putc(c,f);
                fputs("\n\n\n",f);
                fclose(f);
                printf("\nTo EXIT press e| To CONTINUE PRESS C");
                scanf(" %c",&a);
                if(a=='e')
                        break;
        }
        main();
}
void searchstudent()
{
        system("clear");
 printf("\n\n\n\n\t\t\t\t\t\t\t_______ S E A R C H  S T U D E N T _______\n");
        char rollnumber[25];
        char c;
        FILE *f;
        printf("\nEnter students roll number:");
        scanf("%s",rollnumber);
        strcat(rollnumber,".txt");
        f=fopen(rollnumber,"r");
        if(f!=NULL){
                while((c=getc(f))!=EOF)
                        putchar(c);
                        fclose(f);
        }
        else{
                printf("THE STUDENT WITH GIVEN ROLLNUMBER DOES NOT EXIST \n");
                printf(" _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ \n");
                printf("|Enter 'm' to go to MAIN MENU     |\n");
                printf("|Enter 'e' to EXIT                |\n");
                printf("|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|\n");
                printf("\nENTER HERE :");
        scanf(" %c",&c);}
        if(c=='m')
        main();
}
void uploadattendance(){
        FILE *f;
        char rollnumber[20];
        char c;
        printf("\nEnter students rollnumber :");
        scanf("%s",rollnumber);
        strcat(rollnumber,"a.txt");
        system("clear");
        f=fopen(rollnumber,"w");
        printf("\t\t\t\t\t\t\tN O T E : press ctrl+d to confirm\n\n");
        fputs("\t\t\t\t__________ S T U D E N T  A T T E N D A N C E _________\n\n\n\n",f);
        printf("Enter month :");
        fputs("\nM O N T H :",f);
        while((c=getchar())!=EOF)
                putc(c,f);
        fputs("\n\n",f);
        fclose(f);
        f=fopen(rollnumber,"a");
        printf("\nEnter attendance till date :");
 fputs("\nATTENDANCE :",f);
        while((c=getchar())!=EOF)
                putc(c,f);
        fputs("\n\n\n",f);
        fclose(f);
        main();
}
void viewattendance(char * rollnumber){
        FILE *f;
        char c;
        strcat(rollnumber,"a.txt");
        f=fopen(rollnumber,"r");
        while((c=getc(f))!=EOF)
                putchar(c);
        fclose(f);
        printf(" _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _\n");
        printf("|Enter 'm' to RETURN TO MAIN MENU |\n");
        printf("|Enter 'e' to EXIT                |\n");
        printf("|_ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _|\n");
        printf("\nENTER HERE :");
        scanf(" %c",&c);
        if(c=='m')
        main();
}
