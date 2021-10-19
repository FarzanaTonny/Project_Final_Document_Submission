=====================================
Source Code
=====================================

#include<iostream>
 #include<bits/stdc++.h>
#include<fstream>
#include<conio.h>
#include<time.h>
#include<dos.h>
#include<windows.h>
#include<MMSystem.h>
#include<string.h>
#include<stdlib.h>
#include <sstream>




using namespace std;

time_t now;
struct tm *rn;



int i,p,n,hr,mins,tday,tmon,tyear, day[500],mon[500],year[500], rem_no=0, rem_x=0, tmp_hr, dmy=0;
int t_hr[1000],t_min[1000], format_hr[1000], exp_d[500], exp_w[500], exp_m[500], exp_index=0, exp_today, exp_seven[500],exp_thirty[500];
char s[500],s2,str[500][500], ttxx[500][500], am_pm;
string text[500], tmp_text, exp_dtx[500],exp_wtx[500],exp_mtx[500];

// timediffrence

// timediffrence




class student
{
	protected:
	char message[100];
	 char time[50];
	char date[60];
	public:
	void getdata();
	void showdata();
	friend void write();


};
// global variables
int k=0;
fstream obj;
student st;
// Declaration of All non class functions
void viewall();
void mainmenu();
void deleteall();
void reminder();
void exit();

void addexp();
void totalexp();

//Add Task
void write(){
	
		st.getdata();

}



bool rightNow(int a, int b){

int lp=1;
while(lp!=2){ lp++;
time(&now);
rn=localtime(&now);

int hour = rn->tm_hour;
int mins = rn->tm_min;

if(a>=hour) {
    if(a==hour){
     if(b>=mins) return true; else return false;
    }else return true;
        }else return false;

}


}


void student :: getdata()
{
	system("cls");

	SYSTEMTIME t;
    GetLocalTime(&t);


fix_date:
    printf("Please enter a date > or = today in Day-mon-year format:\n");
    scanf("%d-%d-%d",&tday,&tmon,&tyear);

    if(tyear>=t.wYear) {
            if(tyear>t.wYear) {}
                else if  (tmon>=t.wMonth){
                    if  (tmon>t.wMonth) {}
                        else if  (tday>=t.wDay){
                        if(tday>t.wDay  ) {} else {}

                }  else goto fix_date;
                }
                else goto fix_date;
                 }
    else goto fix_date;

rem_limit:
    printf("\n\nhow many Tasks you want to add for that day?\n");
    scanf("%d",&n); if(n>100) { printf("max 100 Tasks per day"); goto rem_limit; }

	 for(i=(rem_no-rem_x); i<(n+rem_no-rem_x); i++)
    {
        day[i]=tday; mon[i]=tmon; year[i]=tyear;
        printf("\n\nReminder : %d\n",i+1);




        chk_hour:
        printf("\nEnter hour:min\n");
        scanf("%d:%d",&hr,&mins);


        if(hr>12)
        { getchar();
            printf("Please use 12 hour format\n"); goto chk_hour;
        }



        if(mins>=60) {
            getchar();
            printf("minutes must be less than 60\n"); goto chk_hour;
        }





        printf("Please enter the time format AM or PM\n");
        getchar();
        scanf("%c%c",&s[i],&s2);
        getchar();

        if(s[i]=='a'||s[i]=='A')
        {
            if(hr==12) {
                 format_hr[i]=hr;
                hr=hr-12;
            }
            else format_hr[i]=hr;

        }


        else  if(s[i]=='p'|| s[i]=='P'){
        if(hr<12){

            format_hr[i]=hr;
           hr=hr+12;
        }

    }

        // check if time is less than right now time

        format_hr[i]=hr;

        t_hr[i]=hr;
        t_min[i]=mins;



         printf("Enter the event name to remind:\n");
        gets(str[i]);

        text[i]=str[i];





    } rem_no=(n+rem_no); n=rem_no-rem_x; dmy++;

     printf("\n\nTasks saved!\n");
         cout<<"\n Press k for Main Menu\n";
	if(_getch()=='k')
		mainmenu();

}



int clock(int a,int b,char str[])

{
    int j,loop=0;
    system("cls");
    while(loop!=1)
    {
        time(&now);
        rn=localtime(&now);




        if(a==rn->tm_hour & b==rn->tm_min)
        {
            tmp_text=text[0];
            for(p=0;p<n-1;p++){

            format_hr[p]=format_hr[p+1];
            t_min[p]=t_min[p+1];
            text[p]=text[p+1];

             day[p]=day[p+1];
              mon[p]=mon[p+1];
               year[p]=year[p+1];
               s[p]=s[p+1];

            }  n=n-1; rem_x++;

            if(a>12) { a=a-12; am_pm='p'; } else  am_pm='a';

            printf("Right now your event is : %s\nTime - %d:%d%cm",tmp_text.c_str(),a,b,s[0]);
            for(j=0;j<2;j++)
            {
            Beep(500,900);
            Beep(700,800);Beep(500,900);

            Sleep(1000);
            } //mainmenu();
            loop=1;

            //getchar(); 30 09 2021

            system("cls");


             cout<<"\n\n\n   Press k to stop and goto Main Menu\n";
	if(_getch()=='k')
		mainmenu();


        }
        else
            free(rn);

    }
}


void sort_dmy_hr_mins(){

  int tmd2=day[i];
            day[i]=day[p+1];
            day[p+1]=tmd2;

                     int tmm=mon[i];
            mon[i]=mon[p+1];
            mon[p+1]=tmm;


            int tmy=year[i];
            year[i]=year[p+1];
            year[p+1]=tmy;


            int tmp=format_hr[i];
            format_hr[i]=format_hr[p+1];
            format_hr[p+1]=tmp;



            int tmp2=t_min[i];
            t_min[i]=t_min[p+1];
            t_min[p+1]=tmp2;




            string tmp3=text[i];
            text[i]=text[p+1];
            text[p+1]=tmp3;


            char tmp4=s[i];
            s[i]=s[p+1];
            s[p+1]=tmp4;

}

void sort_rems(){


             // day month year check

            for(i=0;i<n;i++) {
	           for(p=i;p<n-1;p++) {
            if ( year[i]>year[p+1] ) {

                sort_dmy_hr_mins();


              }

              else if(year[i]==year[p+1]){
                  if(mon[i]>mon[p+1]){

                     sort_dmy_hr_mins();

                  }

                  else if(mon[i]==mon[p+1]){
                        if(day[i]>day[p+1]){

                         sort_dmy_hr_mins();

                  } }

              }



                 } }

            // day month year check


// same day check

             for(i=0;i<n;i++) {
	           for(p=i;p<n-1;p++) {
                    if(year[i]==year[p+1] && mon[i]==mon[p+1] && day[i]==day[p+1])
            if(s[i]=='p' && s[p+1]=='a') {  //cout<<format_hr[i]<<"pm....am"<<format_hr[p+1]<<endl;
            int tmp=format_hr[i];
            format_hr[i]=format_hr[p+1];
            format_hr[p+1]=tmp;

           // cout<<format_hr[i]<<"pm....am"<<format_hr[p+1]<<endl;



            int tmp2=t_min[i];
            t_min[i]=t_min[p+1];
            t_min[p+1]=tmp2;




            string tmp3=text[i];
            text[i]=text[p+1];
            text[p+1]=tmp3;


            char tmp4=s[i];
            s[i]=s[p+1];
            s[p+1]=tmp4;

            }  }   }
// ends of am->pm


 for(i=0;i<n;i++) {
	           for(p=i;p<n-1;p++) {

                if(year[i]==year[p+1] && mon[i]==mon[p+1] && day[i]==day[p+1])
            if ((s[i]=='p' && s[p+1]=='p') || (s[i]=='a' && s[p+1]=='a') )
            if(format_hr[i]>format_hr[p+1]) {
            int tmp=format_hr[i];
            format_hr[i]=format_hr[p+1];
            format_hr[p+1]=tmp;



            int tmp2=t_min[i];
            t_min[i]=t_min[p+1];
            t_min[p+1]=tmp2;




            string tmp3=text[i];
            text[i]=text[p+1];
            text[p+1]=tmp3;

            }  }   }
//
            for(i=0;i<n;i++)
             for(p=i;p<n-1;p++) {
                    if(year[i]==year[p+1] && mon[i]==mon[p+1] && day[i]==day[p+1])
                    if ((s[i]=='p' && s[p+1]=='p') || (s[i]=='a' && s[p+1]=='a') )
            if(format_hr[i]==format_hr[p+1])
                if(t_min[i]>t_min[p+1]){
            int tmp=t_min[i];
            t_min[i]=t_min[p+1];
            t_min[p+1]=tmp;



            string tmp3=text[i];
            text[i]=text[p+1];
            text[p+1]=tmp3;


            }
             }



}



void reminder(){

    sort_rems();

     SYSTEMTIME t;
    GetLocalTime(&t);

    for(i=0;i<n;i++){
    if(tyear==t.wYear && tmon==t.wMonth && tday==t.wDay )
    {




            clock(format_hr[i],t_min[i],str[i]);


    }

    else {
        printf("\nYou have no nTask today"); break;
        }



    }  cout<<"\n\n   Press k to goto Main Menu\n";
	if(_getch()=='k')
		mainmenu();


    //mainmenu();
}














void exit(){
	system("cls");


	Sleep(3000);
	exit(0);
}


//View All Task
void viewall(){
	system("cls");


    sort_rems();

	 cout<<"Saved Tasks...\n\n";
	for(i=0;i<n;i++){


if(format_hr[i]>12) { tmp_hr=format_hr[i]-12; } else if(format_hr[i]==0) tmp_hr=12; else tmp_hr=format_hr[i];

           cout<<"Task "<<i+1<<": "<<text[i]<<endl;;
	cout<<"Time : "<<tmp_hr<<":"<<t_min[i]<<s[i]<<"m"<<endl;
	cout<<"Date : "<<day[i]<<"-"<<mon[i]<<"-"<<year[i]<<endl; cout<<"\n\n";
}




	cout<<"\n\n\n   Press k for Main Menu\n";
	if(_getch()=='k')
		mainmenu();
	else viewall();
	}


// Delete Task
void deleteall(){

	system("cls"); int tasks_cnt=0, task_no;

	sort_rems();

	 cout<<"All Tasks...\n\n";
	for(i=0;i<n;i++){ tasks_cnt++;
if(format_hr[i]>12) { tmp_hr=format_hr[i]-12; } else if(format_hr[i]==0) tmp_hr=12; else tmp_hr=format_hr[i];
    cout<<"Task "<<i+1<<": "<<text[i]<<endl;;
	cout<<"Time : "<<tmp_hr<<":"<<t_min[i]<<s[i]<<"m"<<endl;
	cout<<"Date : "<<day[i]<<"-"<<mon[i]<<"-"<<year[i]<<endl; cout<<"\n\n";
}
	//
	deltsk:
	    cout<<"\n\n\t\t press k for main menu d for continue delete.."<<endl;
	if(_getch()=='k'){
	//Sleep(2000);
	mainmenu();
	} else
	cout<<"\n\n\t\t Press the task number you want to delete.. "<<endl;
	 scanf("%d",&task_no);
	 if(task_no<=tasks_cnt){

        for(i=0;i<n;i++){
         if(task_no==(i+1)){
          for(p=task_no-1;p<n-1;p++){

          format_hr[p]=format_hr[p+1];
            t_min[p]=t_min[p+1];
            text[p]=text[p+1];

             day[p]=day[p+1];
              mon[p]=mon[p+1];
               year[p]=year[p+1];
               s[p]=s[p+1];


          } n=n-1;

         }

        }


	 } else{cout<<"\n\t\tInvalid task number!\n "<<endl; goto deltsk;}




cout<<"\n\n\t\t Task deleted!!!"<<endl;
	///
	cout<<"\n\n\t\t press k for main menu "<<endl;
	if(_getch()=='k'){
	//Sleep(2000);
	mainmenu();
	}
	else
		deleteall();
}



//Add exp
void addexp(){ system("cls");  SYSTEMTIME t; GetLocalTime(&t);

   for(i=0;exp_m[i]!=NULL;i++){}
                 exp_index=i;
  printf("\nEnter Expense amount\n");
        scanf("%d",&exp_d[exp_index]);

        exp_w[exp_index]=exp_d[exp_index];
        exp_m[exp_index]=exp_d[exp_index];

            getchar();
         printf("\nType Expense purpose..\n");
        gets(ttxx[exp_index]);
                exp_dtx[exp_index]=ttxx[exp_index];
                exp_wtx[exp_index]=exp_dtx[exp_index];
                exp_mtx[exp_index]=exp_dtx[exp_index];



//getchar();
            exp_today=t.wDay; exp_seven[exp_index]=t.wDay, exp_thirty[exp_index]=t.wMonth;
         printf("\n\nExpense saved!\n");
         cout<<"\n Press k for Main Menu\n";
	     if(_getch()=='k')
		 mainmenu();

}




// Daiy, weekly, monthly Expenses
void exp_day(){ system("cls");  SYSTEMTIME t; GetLocalTime(&t);
cout<<"Today's Expenses:\n\n\n";
for(i=0;exp_d[i]!=NULL;i++){}
int arrSize = i;
int total_d_exp=0;
if(t.wDay!=exp_today){ arrSize=0; printf("No expense to show!"); }

 for(i=0;i<arrSize;i++){
 cout<<"Expense "<<i+1<<":\nPurpose:"<<exp_dtx[i]<<"\nAmount:"<<exp_d[i]<<"\n\n";  total_d_exp=total_d_exp+exp_d[i];
}
 printf("-----------------------------------------------------------------------------------------\nTotal Expense = %d",total_d_exp);
cout<<"\n\n Press k for Main Menu\n";
	     if(_getch()=='k')
		 mainmenu();
}


void exp_week(){ system("cls"); SYSTEMTIME t; GetLocalTime(&t);

for(i=0;exp_w[i]!=NULL;i++){}
int arrSize2 = i;

int total_w_exp=0;

for(p=0;p<500; p++)
    if(t.wDay-exp_seven[i]==7 || t.wDay-exp_seven[i]==(-23) ){ for(i=0;i<arrSize2;i++){
 cout<<"Expense "<<i+1<<":\nPurpose:"<<exp_wtx[i]<<"\nAmount:"<<exp_w[i]<<"\n\n";  total_w_exp=total_w_exp+exp_w[i];
} }

if(total_w_exp==0){
cout<<"Weekly expense will be available when week ends:\n";
cout<<"\n\n Press k for Main Menu\n";
	     if(_getch()=='k')
		 mainmenu();
}

}


void exp_mon(){ system("cls"); SYSTEMTIME t; GetLocalTime(&t);
for(i=0;exp_m[i]!=NULL;i++){}
int arrSize3 = i;

int total_m_exp=0;

for(p=0;p<500; p++)
    if(t.wMonth!=exp_thirty[i] && exp_thirty[i]!=NULL){ for(i=0;i<arrSize3;i++){
 cout<<"Expense "<<i+1<<":\nPurpose:"<<exp_mtx[i]<<"\nAmount:"<<exp_m[i]<<"\n\n";  total_m_exp=total_m_exp+exp_m[i];
} }

if(total_m_exp==0){
cout<<"Monthly expense will be available when Month ends:\n";
cout<<"\n\n Press k for Main Menu\n";
	     if(_getch()=='k')
		 mainmenu();
}

}


//Total exp
void totalexp(){ system("cls");
cout<<" \n\t\t 1.Daily Expense\n\t\t 2.Weekly Expense\n\t\t 3.Monthly Expense\n\t\t 4.Main menu";
	char chr;
	switch(chr=_getch()){

	case '1':
		exp_day();
		break;
	case '2':
		exp_week();
		break;
	case '3':
	    exp_mon();
	    break;
	    case '4':
	    mainmenu();
	    break;

	default :
		totalexp();
		break;
	}
}


void mainmenu(){



	system("cls");

	//reminder();

	//cout<<"\t\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2 Main Menu \xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2 \n";
		cout<<"\t\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2 Main Menu \xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\xB2\n\n";
        cout<<" \n\t\t 1. Add Tasks\n\t\t 2. View All Tasks\n\t\t 3. Delete Tasks\n\t\t 4. Add today's expense\n\t\t 5. View total expense\n\t\t 6. Exit\n\t\t 7. Activate Reminder\n\n";
		cout<<"\t\t Please select from the above: ";

	char ch;
	switch(ch=_getch()){

	case '1':
		write();
		break;
	case '2':
		viewall();
		break;
	case '3':
	    deleteall();
		break;
            case '4':
	    addexp();
		break;
			case '5':
	    totalexp();
		break;
	case '6':
		exit();
		break;

		case '7':
		reminder();
		break;

	default :
		mainmenu();
		break;
	}




}



	int main()
	{



		mainmenu(); cout<<"\a";
		sort_rems();

		// alarm A;  A.getTime(19,15);  A.start_alarm(); 01 10 2021


		_getch();
		return 0;

	}


==========================================
How To Run The Code
==========================================

First, the user needs to add a task. For this you have to press option 1 of the main menu page.
So first you have to input today's date.User have to input how many tasks he wants to assign.
You have to mention the specific time and name of the task for each task.Then the user can go to
the main menu if he wants.

Second, the user can see the assigned tasks by going to the view all task option. For that he has
to press option 2 of main menu page.

Thirdly, if the user wants,he can delete the assigned task at his own will. For that,you have to
press option 3 of the main menu page.By inputting the task number,the user can delete any task.

Fourthly, every task added by the user has to be activated by pressing option 7 on the main menu
page.

Fifth, if the user wants to keep track of his daily expense,he has to press option 4 of the main
menu page. By giving input amount and expense purpose input, he will be able to add his daily
expense.

Sixth, if user want to see daily,weekly,monthly expense, he has to press option 5 of the main menu
page.There, by pressing any option of daily expense, weekly expense, monthly expense user can see 
the total daily, weekly, monthly expenses respectively.

Lastly, the user can exit the system by pressing option 6 on the main menu page. 