# Superdigit
This project calculates superdigit.
#include <stdio.h>
#include <math.h>

long superDigit(long long m) {
  if(m<10){
    return m;
  }
  else{
    int s = 0;
    do {
      s += m % 10;
      m = m / 10;
    }while (m > 0);
    return superDigit(s);
  }
}


int main()
{
    int n;
    int k;
    printf("Please enter a number (n=) : ");
    scanf("%d",&n);
    printf("Please enter repetition factor (k=) : ");
    scanf("%d",&k);

    int digitOfn = 0;
    int temp =n;
     while (temp>0) {
        digitOfn++;
        temp=temp/10;
    }

    int elements[digitOfn];
    int i = 0;
    int temp2=n;
    while(temp2>0){
        elements[i]=temp2%10;
        temp2=temp2/10;
        i++;
    }
    double newNumber=0;
    int ab = digitOfn*k;
    for(int i = 0; i<k; i++){
        for(int j = digitOfn; j>0; j--){
        newNumber = newNumber + (elements[j-1])*pow(10,ab-1);
        ab--;
        }
    }



    printf("Super digit of number ");
    printf("%.0f", newNumber);
    printf(" is ");
    printf("%d",superDigit(newNumber));

    return 0;
}
