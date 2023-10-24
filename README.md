
#include<stdio.h>
#include<conio.h>
#include<stdlib.h>
#include<string.h>


typedef struct{
	char name[50];
	int bus_num;
	int num_of_seats;
}




void reservation(void);
void viewdetails(void);
void printticket(char name[],int,int,float);
void specificbus(int);
float charge(int,int);



int main()

{
		system("cls");
	printf("\t\t|           BUS TICKET RESERVATION SYSTEM           |\n");
    printf("\t\t|               NAGA SAI CHARAN                         |\n");
    printf("\t\t|                          RA2111028010183            |\n");
    printf("\t\t------------------------------------------------------\n");
    printf("\t\t---------------press any key to continue--------------\n");
    printf("\t\t------------------------------------------------------\n");
	getch();
    system("cls");
	int menu_choice,choice_return;
	start:
	system("cls");
	printf("\n=================================\n");
	printf("    BUS RESERVATION SYSTEM");
	printf("\n=================================");
	printf("\n1>> Reserve A Ticket");
	printf("\n------------------------");
	printf("\n2>> View All Available Bus");
	printf("\n------------------------");
	printf("\n3>> Exit");
	printf("\n------------------------");
	printf("\n\n-->");
	scanf("%d",&menu_choice);
	switch(menu_choice)
	{
		case 1:
			reservation();
			break;
		case 2:
			viewdetails();
			printf("\n\nPress any key to go to Main Menu..");
			getch();
			break;
		case 3:
			return(0);
		default:
			printf("\nInvalid choice");
	}
	goto start;
	return(0);
}

void viewdetails(void)
{
	system("cls");
	printf("\nBUS.No\tBUS Name\t\t\tDestinations\t\tfare\t\tTime\n");
	printf("\n100001\tBus A\tKakinada to Pune\t\t       Rs.5000\t\t9pm");
	printf("\n200002\tBus B\tHyderabad to kerala\t\t       Rs.4000\t\t9am");
	printf("\n300003\tBus C\tBangalore to Mumbai\t\t   Rs.5000\t\t12pm");
	printf("\n400004\tBus D\tKerala to Delhi\t\t       Rs.10500\t\t8am");
	printf("\n500005\tBus E\tChennai to Nellore\t\t  Rs.1000\t\t11am");
	printf("\n600006\tBus F\tVijayawada to Warangal\t\tRs.2000\t\t7am");
	printf("\n700007\tBus G\tVizag to Chennai \t\tRs.3000\t\t10am");
	printf("\n800008\tBus H\tMadhya pradesh to Bihar \t\tRs.5000\t\t10pm");

}


void reservation(void)
{
	char confirm;
	int i=0;
	float charges;
	pd passdetails;
	FILE *fp;
	fp=fopen("seats_reserved.txt","a");
	system("cls");

	printf("\nEnter Your Name:> ");
	fflush(stdin);
	gets(passdetails.name);

	printf("\nEnter Number of seats:> ");
	scanf("%d",&passdetails.num_of_seats);
	printf("\n\n>>Press Enter To View Available Bus<< ");
	getch();
	system("cls");
	viewdetails();
	printf("\n\nEnter bus number:> ");
	start1:
	scanf("%d",&passdetails.bus_num);
	if(passdetails.bus_num>=100001 && passdetails.bus_num<=800008)
	{
		charges=charge(passdetails.bus_num,passdetails.num_of_seats);
		printticket(passdetails.name,passdetails.num_of_seats,passdetails.bus_num,charges);
	}
	else
	{
		printf("\nInvalid bus Number! Enter again--> ");
		goto start1;
	}

	printf("\n\nConfirm Ticket (y/n):>");
	start:
	scanf(" %c",&confirm);
	if(confirm == 'y')
	{
		fprintf(fp,"%s\t\t%d\t\t%d\t\t%.2f\n",&passdetails.name,passdetails.num_of_seats,passdetails.bus_num,charges);
		printf("==================");
		printf("\n Reservation successful\n");
		printf("==================");
		printf("\nPress any key to go back to Main menu");
	}
	else
	{
		if(confirm=='n'){
			printf("\nReservation Not Done!\nPress any key to go back to  Main menu!");
		}
		else
		{
			printf("\nInvalid choice entered! Enter again-----> ");
			goto start;
		}
	}
	fclose(fp);
	getch();
}

float charge(int bus_num,int num_of_seats)
{
		if (bus_num==100001)
	{
		return(5000.0*num_of_seats);
	}
	if (bus_num==200002)
	{
		return(4000.0*num_of_seats);
	}
	if (bus_num==300003)
	{
		return(5000.0*num_of_seats);
	}
	if (bus_num=400004)
	{
		return(10500.0*num_of_seats);
	}
	if (bus_num==500005)
	{
		return(1000.0*num_of_seats);
	}
	if (bus_num==600006)
	{
	    return(2000.0*num_of_seats);
	}
	if (bus_num==700007)
	{
	    return(3000.0*num_of_seats);
	}
	if (bus_num==800008)
	{
	    return(5000.0*num_of_seats);
	}

}

void printticket(char name[],int num_of_seats,int bus_num,float charges)
{
	system("cls");
	printf("-------------------\n");
	printf("\tTICKET\n");
	printf("-------------------\n\n");
	printf("Name:\t\t\t%s",name);
	printf("\nNumber Of Seats:\t%d",num_of_seats);
	printf("\nBus Number:\t\t%d",bus_num);
	specificbus(bus_num);
	printf("\nCharges:\t\t%.2f",charges);
}

void specificbus(int bus_num)
{

	if (bus_num==100001)
	{
		printf("\nBus:\t\t\tBUS A");
		printf("\nDestination:\t\tKakinada to Pune");
		printf("\nDeparture:\t\t9pm ");
	}
	if (bus_num==200002)
	{
		printf("\nBus:\t\t\tBUS B");
		printf("\nDestination:\t\tHyderabad to kerala");
		printf("\nDeparture:\t\t9am");
	}
	if (bus_num==300003)
	{
		printf("\nBus:\t\t\tBUS C");
		printf("\nDestination:\t\tBangalore to Mumbai");
		printf("\nDeparture:\t\t12pm");
	}
	if (bus_num==400004)
	{
		printf("\nBus:\t\t\tBUS D");
		printf("\nDestination:\t\tKerala to Delhi");
		printf("\nDeparture:\t\t8am ");
	}
	if (bus_num==500005)
	{
		printf("\nBus:\t\t\tBUS E");
		printf("\nDestination:\t\tChennai to Nellore");
		printf("\nDeparture:\t\t11am");
	}
	if (bus_num==600006)
	{
		printf("\nBus:\t\t\tBUS F");
		printf("\nDestination:\t\tVijayawada to Warangal");
		printf("\nDeparture:\t\t7am");
	}
	if (bus_num==700007)
	{
		printf("\nBus:\t\t\tBUS G");
		printf("\nDestination:\t\tVizag to Chennai");
		printf("\nDeparture:\t\t10am");
	}
	if (bus_num==800008)
	{
		printf("\nBus:\t\t\tBUS H");
		printf("\nDestination:\t\tMadhya pradesh to Bihar");
		printf("\nDeparture:\t\t10pm");
	}

}
