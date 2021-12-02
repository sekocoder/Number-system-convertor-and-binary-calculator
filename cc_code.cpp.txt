/* Program to perform number system conversions and binary operations */

#include <stdio.h>
#include <math.h>

void b2d();               /*Protoype for Binary to decimal function*/
void o2d();               /*Protoype for Octal to decimal function*/
void h2d();               /*Protoype for Hexadecimal to decimal function*/
void d2b(long int);       /*Protoype for Decimal to Binary function*/
void d2o(long int);       /*Protoype forDecimal  to Octal function*/
void d2h(long int);       /*Protoype for Decimal to Hexadecimal function*/
void bAdd();              /*Protoype for binary addition function*/
void bSubtract();         /*Protoype for binary Subtraction function*/
void bitwise();           /*Protoype for bitwise operations */
long int bob2d(long int); /*Prototype for function for conversion of binary input into decimal for bitwise operations*/

long int d = 0; /*global variable d*/

int main() /*main function*/

{
    int ch1, ch2, ch3, ch4, ch5, ch6, ch7;

Mlabel:

    printf("\n\n\n\n\t\t *********** Welcome To Number System Converter And Binary Operations Calculator *********** \n\n");
    printf("\n\n For Number System Conversion press 1\n");
    printf("\n For Binary Operations press 2\n");
    printf("\nEnter your choice : ");

    scanf("%d", &ch4);

    switch (ch4)
    {
    case 1: /*For conversions*/

        printf("\n\n\t\t ***********Number System Converter ***********\n");

    c1: /*Block for first choice*/

        printf("\n\n In which system you want to enter the number as input :\n\n");
        printf("\tFor Binary press : 1 \n");
        printf("\tFor Octal press : 2\n");
        printf("\tFor Hexadecimal press : 3\n");
        printf("\tFor Decimel press : 4\n");
        printf("\nEnter your choice(1,2,3,4) : ");

        scanf("%d", &ch1); /*For input of user's choice */

        if (ch1 != 1 && ch1 != 2 && ch1 != 3 && ch1 != 4)
        {
            printf("\nInvalid choice '%d'..Please a enter valid choice", ch1);
            goto c1;
        }

    c2: /*Block for second choice*/

        printf("\n In which system you want to convert the number which you entered :\n");
        printf("\n\tFor Binary press :1 \n");
        printf("\tFor Octal press : 2\n");
        printf("\tFor Hexadecimal press : 3\n");
        printf("\tFor Decimel press : 4\n");
        printf("\nEnter your choice(1,2,3,4) : ");

        scanf("%d", &ch2); /*For input of user's choice */

        if (ch2 != 1 && ch2 != 2 && ch2 != 3 && ch2 != 4)
        {
            printf("\nInvalid choice '%d' ..Please a enter valid choice\n", ch2);
            goto c2;
        }

        printf("\n");

        if (ch1 == ch2)
        {
            printf("Please enter a choice other than '%d' for different number system than the one in which your input is for conversion.. \n", ch1);
            goto c2;
        }

        else

        {
            switch (ch1) /*switch case for calling or performing a specific function according to user's choice*/

            {
            case 1:
                b2d(); /* Function to convert Binary to decimal is called */
                break;

            case 2:
                o2d(); /* Function to convert Octal to decimal is called */
                break;

            case 3:
                h2d(); /* Function to convert Hexadecimal to decimal is called */
                break;

            case 4:
                printf("Enter the decimel number : ");
                scanf("%ld", &d);
                break;
            }

            switch (ch2) /*switch case for calling or performing a specific function according to user's choice*/
            {

            case 1:
                d2b(d); /* Function to convert Decimal to Binary is called */
                break;

            case 2:
                d2o(d); /* Function to convert Decimal to Octal is called */
                break;

            case 3:
                d2h(d); /* Function to convert Decimal to Hexadecimal  is called */
                break;

            case 4:
                printf("\nThe decimel number is : %ld", d);
                break;
            }
        }
        printf("\n\n\tIf you want to continue (Press 1) for yes and (Press any other integer like 0) for no : ");
        scanf("%d", &ch3);
        if (ch3 == 1)
            goto Mlabel; /* To ensure program does not terminate after one operation */
        else
            break;

    case 2: /*For binary operations*/

        printf("\n\n\t\t ***********Binary Operatins Calculator***********\n");

        printf("\nFor Addition of binary number press : 1\n");
        printf("For Subtraction of binary number press : 2\n");
        printf("For Bitwise operations press : 3\n");
        printf("Enter your choice : ");

        scanf("%d", &ch5);

        if (ch5 == 1)

            bAdd(); /*the binary addition function is called*/

        else if (ch5 == 2)

            bSubtract(); /*the binary subtraction function is called*/

        else if (ch5 == 3)

            bitwise(); /* bitwise operator on binary is called */

        else

            printf("Invalid input");

        printf("\n\n\tIf you want to continue (Press 1) for yes and (Press any other integer like 0) for no : ");

        scanf("%d", &ch6);

        if (ch6 == 1)
            goto Mlabel; /* To ensure program does not terminate after one operation */
    }

    printf(" \n\n\n\t\t\t\t********** Thank You ********** "); /*end message*/

    return 0;
}

void b2d() /* Definition of Function to convert Binary to decimal */
{
    long int num;
    printf("Enter the Binary number (0 and 1): ");
    scanf("%ld", &num);
    long int rem, sum = 0, power = 0;
    while (num > 0)
    {
        rem = num % 10;
        num = num / 10;
        sum = sum + rem * pow(2, power);
        power++;
    }

    d = sum;
}

void o2d() /* Definition of Function to convert Octal to Decimal */
{
    long int octal, decimal = 0;
    int i = 0;

    printf("Enter any octal number: ");

    scanf("%ld", &octal);

    while (octal != 0)
    {
        decimal = decimal + (octal % 10) * pow(8, i++);

        octal = octal / 10;
    }

    d = decimal;
}

void h2d() /* Definition of Function to convert Hexadecimal to Decimal */
{
    long int decnum = 0, rem, i = 0, len = 0;
    char hexnum[20];

labl:
    printf("Enter any Hexadecimal Number: ");
    scanf("%s", hexnum);

    while (hexnum[i] != '\0')
    {
        len++;
        i++;
    }
    len--;
    i = 0;

    while (len >= 0)
    {
        rem = hexnum[len];

        if (rem >= 48 && rem <= 57)
            rem = rem - 48;

        else if (rem >= 65 && rem <= 70)
            rem = rem - 55;

        else if (rem >= 97 && rem <= 102)
            rem = rem - 87;

        else
        {
            printf("\nYou've entered an invalid Hexadecimal digit\n");
            goto labl;
        }

        decnum = decnum + (rem * pow(16, i));
        len--;
        i++;
    }

    d = decnum;
}

void d2b(long int num) /* Definition of Function to convert Decimal to Binary */
{
    long int rem[50], i = 0, length = 0;

    while (num > 0)
    {
        rem[i] = num % 2;
        num = num / 2;
        i++;
        length++;
    }

    printf("\nThe Binary number is : ");

    for (i = length - 1; i >= 0; i--)
        printf("%ld", rem[i]);
}

void d2o(long int num) /* Definition of Function to convert Decimal to Octal */
{
    long int rem[50], i = 0, length = 0;

    while (num > 0)
    {
        rem[i] = num % 8;
        num = num / 8;
        i++;
        length++;
    }

    printf("\nThe Octal number is : ");

    for (i = length - 1; i >= 0; i--)
        printf("%ld", rem[i]);
}

void d2h(long int num) /* Definition of Function to convert Decimal to Hexadecimal */
{
    long int rem[50], i = 0, length = 0;

    while (num > 0)
    {
        rem[i] = num % 16;
        num = num / 16;
        i++;
        length++;
    }

    printf("\nThe Hexadecimal number is : ");

    for (i = length - 1; i >= 0; i--)
    {
        switch (rem[i])

        {
        case 10:
            printf("A");
            break;

        case 11:
            printf("B");
            break;

        case 12:
            printf("C");
            break;

        case 13:
            printf("D");
            break;

        case 14:
            printf("E");
            break;

        case 15:
            printf("F");
            break;

        default:
            printf("%ld", rem[i]);
            break;
        }
    }
}

void bAdd() /*Definition for addition of two binary numbers*/
{
    long binary1, binary2;
    int i = 0, remainder = 0, sum[20], bn1, bn2;

    printf("Enter the first binary number: ");
    scanf("%ld", &binary1);
    printf("Enter the second binary number: ");
    scanf("%ld", &binary2);

    bn1 = binary1;
    bn2 = binary2;
    
    while (binary1 != 0 || binary2 != 0)
    {
        sum[i++] = (binary1 % 10 + binary2 % 10 + remainder) % 2;
        remainder = (binary1 % 10 + binary2 % 10 + remainder) / 2;
        binary1 = binary1 / 10;
        binary2 = binary2 / 10;
    }
    if (remainder != 0)
        sum[i++] = remainder;
    --i;
    printf("Sum of the numbers in binary form is : ");
    while (i >= 0)
        printf("%d", sum[i--]);
    printf("\n");

    long int rem1, sum1 = 0, power1 = 0;
    int s1 = 0, s3;
    while (bn1 > 0)
    {
        rem1 = bn1 % 10;
        bn1 = bn1 / 10;
        sum1 = sum1 + rem1 * pow(2, power1);
        power1++;
    }
    s1 = sum1;

    long int rem2, sum2 = 0, power2 = 0;
    int s2 = 0;
    while (bn2 > 0)
    {
        rem2 = bn2 % 10;
        bn2 = bn2 / 10;
        sum2 = sum2 + rem2 * pow(2, power2);
        power2++;
    }
    s2 = sum2;

    s3 = s1 + s2;
    printf("The sum of the numbers in decimal form is : %d\n", s3);
}

void bSubtract() /*Definition for subtraction of two binary numbers*/
{
    long int b1, b2;
    printf("Enter the binary number to subtract from : ");
    scanf("%ld", &b1);

    printf("Enter the binary number to subtract : ");
    scanf("%ld", &b2);

    long int rem1, sum1 = 0, power1 = 0;
    int d1, d3;
    while (b1 > 0)
    {
        rem1 = b1 % 10;
        b1 = b1 / 10;
        sum1 = sum1 + rem1 * pow(2, power1);
        power1++;
    }
    d1 = d;
    d1 = sum1;
    d = 0;

    long int rem2, sum2 = 0, power2 = 0;
    int d2;
    while (b2 > 0)
    {
        rem2 = b2 % 10;
        b2 = b2 / 10;
        sum2 = sum2 + rem2 * pow(2, power2);
        power2++;
    }
    d2 = d;
    d2 = sum2;
    d = 0;

    d3 = d1 - d2;
    printf("\nThe difference between the numbers in decimal form is : %d\n", d3);

    long int rem[50], i = 0, length = 0;
    while (d3 > 0)
    {
        rem[i] = d3 % 2;
        d3 = d3 / 2;
        i++;
        length++;
    }
    printf(" \nThe difference between the numbers in binary form is : ");

    for (i = length - 1; i >= 0; i--)
        printf("%ld", rem[i]);
    printf("\n");
}

void bitwise() /* Definition of Function to operate biwtise operator on binary numbers */
{
    printf("\nFor AND operation press :1\n");
    printf("For OR operation press :2\n");
    printf("For XOR operation press :3\n");
    printf("Enter your choice : ");
    int ch7;
    scanf("%d", &ch7);

    long int a, b, c, d;

    printf("\nEnter the first binary number: ");
    scanf("%ld", &a);

    c = bob2d(a); /*bob2d function is called*/

    printf("Enter the second binary number: ");
    scanf("%ld", &b);

    d = bob2d(b); /*bob2d function is called*/

    if (ch7 == 1)
        printf("\n  The output of the Bitwise AND operator is %ld", c & d);

    if (ch7 == 2)
        printf("\n  The output of the Bitwise OR operator is %ld", c | d);

    if (ch7 == 3)
        printf("\n  The output of the Bitwise XOR operator is %ld", c ^ d);
}

long int bob2d(long int num) /*Definition of function for conversion of binary input into decimal for bitwise operations*/
{
    long int rem, sum = 0, power = 0;
    while (num > 0)
    {
        rem = num % 10;
        num = num / 10;
        sum = sum + rem * pow(2, power);
        power++;
    }

    return sum;
}
