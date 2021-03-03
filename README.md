# Iv-n-Alonzo-Chapter-6
EXERCISE 1
// Write a program to find the square of the distance between twopoints. (For a more advanced problem, find the actual distance. This problem involves u sing the standard function sqrt. Use your help system to find out more about how to use this function.)

#include <stdio.h>
#include <math.h>

char line[100];
float distance;
float square_of_distance;
float actual_distance;

int main()
{
  printf("Enter the distance between the two points in meters: ");

  fgets(line, sizeof(line), stdin);
  sscanf(line, "%f", &distance);

  square_of_distance = distance * distance;

  printf("The square of the distance is: %f meters\n", square_of_distance);

  actual_distance = sqrt(square_of_distance);

  printf("The actual distance is: %f meters\n", actual_distance);

  return 0;
}

EXERCISE 2
//A professor generates letter grades using Table 6 -3.
//Given a numeric grade, print the letter.

#include <stdio.h>

char line[100];

int percentage;
char grade;

int main()
{
  printf("Enter the percentage: ");

  fgets(line, sizeof(line), stdin);
  sscanf(line, "%d", &percentage);

  if (percentage >= 0 && percentage <= 60) {
    grade = 'F';
  }
  else if (percentage >= 61 && percentage <= 70) {
    grade = 'D';
  }
  else if (percentage >= 71 && percentage <= 80) {
    grade = 'C';
  }
  else if (percentage >= 81 && percentage <= 90) {
    grade = 'B';
  }
  else if (percentage >= 91 && percentage <= 100) {
    grade = 'A';
  }

  printf("The student's grade is: %c\n", grade);

  return 0;
}

EXERCISE 3
// Modify the previous program to print a + or - after the letter grade, based on the last digit of the score. The modifiers are listed in Table 6-4.For example, 81=B-, 94=A, and 68=D+. Note: An F is only an F. There is no F+ or F-.

#include <stdio.h>

char line[100];

int percentage;
char grade;
char sign;

int main()
{
  sign = ' ';

  printf("Enter the percentage: ");

  fgets(line, sizeof(line), stdin);
  sscanf(line, "%d", &percentage);

  if (percentage >= 0 && percentage <= 60) {
    grade = 'F';
  }
  else if (percentage >= 61 && percentage <= 70) {
    grade = 'D';

    if (percentage >= 61 &&  percentage <= 63) {
      sign = '-';
    }
    else if (percentage >= 68) {
      sign = '+';
    }
  }
  else if (percentage >= 71 && percentage <= 80) {
    grade = 'C';

    if (percentage >= 71 &&  percentage <= 73) {
      sign = '-';
    }
    else if (percentage >= 78) {
      sign = '+';
    }
  }
  else if (percentage >= 81 && percentage <= 90) {
    grade = 'B';

    if (percentage >= 81 &&  percentage <= 83) {
      sign = '-';
    }
    else if (percentage >= 88) {
      sign = '+';
    }
  }
  else if (percentage >= 91 && percentage <= 100) {
    grade = 'A';

    if (percentage >= 91 &&  percentage <= 93) {
      sign = '-';
    }
    else if (percentage >= 98) {
      sign = '+';
    }
  }

  printf("Grade: %c%c\n", grade, sign);

  return 0;
}

EXERCISE 4
// Given an amount of money (less than $1.00), compute the number of quarters, dimes, nickels, and pennies needed.

#include <stdio.h>

char line[100]; 
float money; 
float money_not_converted;
int quarters = 0;
int dimes = 0;
int nickels = 0;
int pennies = 0;

int main()
{
  printf("Enter the amount of money (less than $1.00): \n");
  fgets(line, sizeof(line), stdin);
  sscanf(line, "%f", &money);

  money_not_converted = money;

  while (money_not_converted > 0.00) {
    if (money_not_converted > 0.24) {
      quarters = quarters + 1;
      money_not_converted = money_not_converted - 0.25 ;
    }
    else if (money_not_converted > 0.09) {
      dimes = dimes + 1;
      money_not_converted = money_not_converted - 0.10;
    }
    else if (money_not_converted > 0.04) {
      nickels = nickels + 1;
      money_not_converted = money_not_converted - 0.05;
    }
    else if (money_not_converted > 0.00){
      pennies = pennies + 1;
      money_not_converted = money_not_converted - 0.01;
    }
  }

  printf("For $%f you need: \n", money);
  printf("%d quarters\n", quarters);
  printf("%d dimes\n", dimes);
  printf("%d nickels\n", nickels);
  printf("%d pennies\n", pennies);

  return 0;
}

EXERCISE 5
// A leap year is any year divisible by 4, unless the year is divisible by 100, but not 400. Write a program to tell if a year is a leap year.

#include <stdio.h>

char line[100];
int year;

int isleap(int year)
{
  int leap = 0;

  if ((year % 4) == 0) {
    leap = 1;

    if ((year % 100) == 0 && (year % 400) != 0) {
      leap = 0;
    }
  }

  return leap;
}

int main()
{
  printf("Enter year: ");

  fgets(line, sizeof(line), stdin);
  sscanf(line, "%d", &year);

  if (isleap(year)) {
    printf("Year %d is a leap year\n", year);
  }
  else {
    printf("Year %d is not a leap year\n", year);
  }

  return 0;
}

EXERCISE 6
// Write a program that, given the number of hours an employee worked and the hourly wage, computes the employee's weekly pay. Count any hours over 40 as overtime at time and a half.

#include <stdio.h>

char  line[100];
int   hours;
float hourly_wage;
float weekly_pay;

float get_weekly_pay(int hours, float hourly_wage) {
  int   overtime;
  float pay;

  if (hours < 41) {
    pay = hours * hourly_wage;
  }
  else {
    overtime = hours - 40;
    pay = 40 * hourly_wage;
    pay = pay + (overtime * (hourly_wage / 2));
  }

  return pay;
}

int main()
{
  printf("Enter the number of hours worked: ");

  fgets(line, sizeof(line), stdin);
  sscanf(line, "%d", &hours);

  printf("Enter the hourly wage of the employee: ");

  fgets(line, sizeof(line), stdin);
  sscanf(line, "%f", &hourly_wage);

  printf("The weekly pay of the employee is: $%f\n", get_weekly_pay(hours, hourly_wage));

  return 0;
}

EXERCISE 7
// Status for an exam (F for failed and P for passed) depending on the grade (-70 for F and +69 for pass )

#include <stdio.h>

char line[100];

int grade;
char exam_status;

int main()
{
  printf("Enter the grade: ");

  fgets(line, sizeof(line), stdin);
  sscanf(line, "%d", &grade);

  if (grade < 70) {
    exam_status = 'F';
  }
  else{
    exam_status = 'P';
  }

  printf("The exam's status is: %c\n", exam_status);

  return 0;
}
