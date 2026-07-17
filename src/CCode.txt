//configurare porturi pentru LCD
sbit LCD_RS at LATB4_bit;
sbit LCD_EN at LATB5_bit;
sbit LCD_D4 at LATB0_bit;
sbit LCD_D5 at LATB1_bit;
sbit LCD_D6 at LATB2_bit;
sbit LCD_D7 at LATB3_bit;

sbit LCD_RS_Direction at TRISB4_bit;
sbit LCD_EN_Direction at TRISB5_bit;
sbit LCD_D4_Direction at TRISB0_bit;
sbit LCD_D5_Direction at TRISB1_bit;
sbit LCD_D6_Direction at TRISB2_bit;
sbit LCD_D7_Direction at TRISB3_bit;

//In cadrul proiectului am schimbat elementul vibrator cu un bec, pentru a fi mai usor de urmarit

void DeschideScurt() //functia care va da un semnal scurt luminos
{
   LATC = 0xFF; delay_ms(150); LATC = 0x00; delay_ms(150);
}

void DeschideLung() //functia care va da un semnal lung luminos
{
   LATC = 0xFF; delay_ms(450); LATC = 0x00; delay_ms(150);
}

void literalumina(char s)
{
if (s == ' ') {delay_ms(1050);} //spatiu 7 unitati intre cuvinte

//litere
if (s=='A' || s == 'a') {DeschideScurt();DeschideLung();}
else if (s=='B' || s == 'b') {DeschideLung(); DeschideScurt(); DeschideScurt(); DeschideScurt();}
else if (s=='C' || s == 'c') {DeschideLung(); DeschideScurt(); DeschideLung(); DeschideScurt();}
else if (s=='D' || s == 'd') {DeschideLung(); DeschideScurt(); DeschideScurt();}
else if (s=='E' || s == 'e') {DeschideScurt();}
else if (s=='F' || s == 'f') {DeschideScurt(); DeschideScurt(); DeschideLung(); DeschideScurt();}
else if (s=='G' || s == 'g') {DeschideLung(); DeschideLung(); DeschideScurt();}
else if (s=='H' || s == 'h') {DeschideScurt(); DeschideScurt(); DeschideScurt(); DeschideScurt();}
else if (s=='I' || s == 'i') {DeschideScurt(); DeschideScurt();}
else if (s=='J' || s == 'j') {DeschideScurt(); DeschideLung(); DeschideLung(); DeschideLung();}
else if (s=='K' || s == 'k') {DeschideLung(); DeschideScurt(); DeschideLung();}
else if (s=='L' || s == 'l') {DeschideScurt(); DeschideLung(); DeschideScurt(); DeschideScurt();}
else if (s=='M' || s == 'm') {DeschideLung(); DeschideLung();}
else if (s=='N' || s == 'n') {DeschideLung(); DeschideScurt();}
else if (s=='O' || s == 'o') {DeschideLung(); DeschideLung(); DeschideLung();}
else if (s=='P' || s == 'p') {DeschideScurt(); DeschideLung(); DeschideLung(); DeschideScurt();}
else if (s=='Q' || s == 'q') {DeschideLung(); DeschideLung(); DeschideScurt(); DeschideLung();}
else if (s=='R' || s == 'r') {DeschideScurt(); DeschideLung(); DeschideScurt();}
else if (s=='S' || s == 's') {DeschideScurt(); DeschideScurt(); DeschideScurt();}
else if (s=='T' || s == 't') {DeschideLung();}
else if (s=='U' || s == 'u') {DeschideScurt(); DeschideScurt(); DeschideLung();}
else if (s=='V' || s == 'v') {DeschideScurt(); DeschideScurt(); DeschideScurt(); DeschideLung();}
else if (s=='W' || s == 'w') {DeschideScurt(); DeschideLung(); DeschideLung();}
else if (s=='X' || s == 'x') {DeschideLung(); DeschideScurt(); DeschideScurt(); DeschideLung();}
else if (s=='Y' || s == 'y') {DeschideLung(); DeschideScurt(); DeschideLung(); DeschideLung();}
else if (s=='Z' || s == 'z') {DeschideLung(); DeschideLung(); DeschideScurt(); DeschideScurt();}

//cifre
if (s == '0') {DeschideLung(); DeschideLung(); DeschideLung(); DeschideLung(); DeschideLung();}
else if (s == '1') {DeschideScurt(); DeschideLung(); DeschideLung(); DeschideLung(); DeschideLung();}
else if (s == '2') {DeschideScurt(); DeschideScurt(); DeschideLung(); DeschideLung(); DeschideLung();}
else if (s == '3') {DeschideScurt(); DeschideScurt(); DeschideScurt(); DeschideLung(); DeschideLung();}
else if (s == '4') {DeschideScurt(); DeschideScurt(); DeschideScurt(); DeschideScurt(); DeschideLung();}
else if (s == '5') {DeschideScurt(); DeschideScurt(); DeschideScurt(); DeschideScurt(); DeschideScurt();}
else if (s == '6') {DeschideLung(); DeschideScurt(); DeschideScurt(); DeschideScurt(); DeschideScurt();}
else if (s == '7') {DeschideLung(); DeschideLung(); DeschideScurt(); DeschideScurt(); DeschideScurt();}
else if (s == '8') {DeschideLung(); DeschideLung(); DeschideLung(); DeschideScurt(); DeschideScurt();}
else if (s == '9') {DeschideLung(); DeschideLung(); DeschideLung(); DeschideLung(); DeschideScurt();}
}

int main()
{
  char txt1[] = "bioinginerie";
  char lit[] = " ";
  int i;
  TRISC = 0; //configuram porturile
  ANSELB = 0;
  Lcd_Init(); // initializam lcd-ul
  Lcd_Cmd(_LCD_CLEAR);
  Lcd_Cmd(_LCD_CURSOR_OFF);
  for(i = 0; i<= strlen(txt1); i++)
  {
    literalumina(txt1[i]); // luminam led-ul in functie de litera
    lit[1] = txt1[i];
    Lcd_Out(1,1,lit); // afisam litera si pe lcd
    delay_ms(450); // spatiu 3 unitati intre litere
  }
  Lcd_Cmd(_LCD_CLEAR);
  Lcd_Out(1,1,txt1); // afisam tot cuvantul pe lcd dupa ce am parcurs literele
}