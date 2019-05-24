import java.util.Scanner;
import java.util.Random;

class Main {
  public static void main(String[] args) {
    //Initializing variables below
    Scanner sc = new Scanner(System.in);
    Words wordPicker = new Words();
    Game scoreCalculator = new Game();
    Game letterSwitcher = new Game();
    Game wordGuessed = new Game();
    String playAgain = null;
    int Highscore = 0;
    int bonusPoints = 0;
    boolean gameIsOver = false;
    String userName = null;
    
    /*
      So the first important thing I needed to figure out when
      I planned on making this game was how I was gonna sort 
      the users guesses and the word. My idea I thought of was 
      using 2 char arrays. One with words the user is guessing, 
      and one with blanks or '_'. My plan was whenever the user
      guessed the letter, since the 2 arrays are the same size, 
      I simply swap places and I have a if statement that sets 
      the game to be over once the entire array has exactly what 
      the word is.  
    */
    char guessedLetters[]; //This array is with blanks
    char notGuessedLetters[]; //This array is where the word is and the user must figure it out

    Game letterChecker = new Game();
    int lettersGuessed = 0;
    int score = 0;
    String word = null;
    int difficulty = 0;
    int lives = 6;
    int wordLength = 0;
    int guesses = 0;
    char letter = ' ';
    //Initializing variables Above
    System.out.println();
    System.out.println("\t\t\tWelcome to Hang Man \n\t\t\t By Edgar Quinones\n");
    System.out.print("Is this your first time playing Hang Man? (Yes or No) ");
    String firstTimePLaying = sc.next();
    if(firstTimePLaying.equalsIgnoreCase("yes"))//If this is the users first time playing, a simple set of instructions are shown
    {
      System.out.println();
      System.out.println("Hang Man is a very simple game anyone can play!\nTo start, pick a difficulty. This will be determined \nby the number you pick from 1 to 4.\nAll you know is how many letters are in it.\nYou only have 6 lives. Good Luck! :)");
    }
  
    do
    {
      //reseting variable values for if the user plays again 
      guesses = 0;
      score = 0;
      gameIsOver = false;
      lives = 6;
      //resets varibles above
      System.out.print("Please enter your username: ");
      userName = sc.next();
      System.out.print("What difficulty would you like to play on "+userName+"?(1-4) ");
      difficulty = sc.nextInt();
      word = wordPicker.pickWord(difficulty);//Using the pickWord method, a word is picked depending on the number, which increases how complex the word is
      wordLength = word.length();//The wordLength int is used to set the size of the arrays used for user guessing
      guessedLetters = new char[wordLength];
      notGuessedLetters = new char[wordLength];
      for(int x = 0; x < wordLength;x++)//This loop will put the the word inside the array
      {
        notGuessedLetters[x] = word.charAt(x);
      }
      for(int x = 0; x < wordLength;x++)//This array will have blanks that the users correct guesses will be entered in
      {
        guessedLetters[x] = '_';
      }
  
      System.out.println("Your word has "+wordLength+" letters in it, Good Luck!");
      for(int y = 0; y<guessedLetters.length;y++)//Blanks are shown for the user so they can figure out size and know what letters they picked
          {
            System.out.print(guessedLetters[y]+" ");
          }
          System.out.println();
      do//Using this do-while loop, game occurs in here
      {

        guesses++;//User knows how many guesses they have 
        System.out.println("Guess "+guesses+":");     
        System.out.print("Please enter a letter: ");
        letter = sc.next().charAt(0);//The user can put 1 letter, however, he can enter the entire word or portions if he knows it as long as there is space in between
        if(!(letterChecker.letterIsInWord(notGuessedLetters, letter) >0))//The letterIsInWord method determines how many of that letter is in the word, used for scoring, if it is not a correct letter, they lose a life and certain things will happen depending on how many lives left the user has.
        {
          lives--;
          if(lives == 1)//An extra warning is shown if user has only 1 life left
          {
            System.out.println("Oh no! Wrong letter! 1 life left! Be careful!");
          }
          else if(lives > 1){
            System.out.println("Oh no! Wrong letter! "+lives+" lives left :(");
          }
          else if (lives == 0)//If user runs out of lives, game ends, user is told what the word ends, and is thanked for playing
          {
            System.out.println("Oh no! No more lives :(. The word was "+word+". You got a score of "+score+". Better luck next time.\n\t\t\tThanks for Playing!");
           
          System.out.println();
          gameIsOver=true;//GameIsOver boolean is used to end the do-while loop
          break;
          }
        }
        else//If the user got a correct guess, the else statement is ran
        {
           System.out.println("You found "+letterChecker.letterIsInWord(notGuessedLetters, letter)+" correct letter(s)");//Using the letterIsInWord method, it tells user how many letters they got in it in case the word has more than one letter in it.
          score += letterChecker.letterIsInWord(notGuessedLetters, letter);//Score is added for each letter added
          for(int x = 0; x < notGuessedLetters.length;x++)//This is where the letterSwitch method is used to put the correctly guessed letter into the new array
      {
        if((letter + " ").equals(notGuessedLetters[x] + " "))//It checks to see if the letter is in array, and switches it using the array
        {
         letterSwitcher.letterSwitch(notGuessedLetters, guessedLetters, x);//Swaps places with letter guessed and blank
         
        } 
   
        }  
        for(int y = 0; y<guessedLetters.length;y++)//prints out everything user has guessed and forwhatever they haven't guessed a blank will appear
          {
            System.out.print(guessedLetters[y]+" ");
          }
          System.out.println();
          
        }
      
        
          if(wordGuessed.wordFound(notGuessedLetters) == true)//The wordFound method is used to determine if the user has guessed the entire word, if thats true, this statement is ran
          {
              bonusPoints = scoreCalculator.calcScore(lives);//based on how many lives left, user will get bonus points using the calcScore method
              score += bonusPoints;//adds bonus to total
              System.out.println("You solved the word! It was "+word+". You ended with a score of "+score+".");
              gameIsOver = true;//GameIsOver boolean is set to true and loop ends
          }

      }while(lives != 0 && !(gameIsOver==true));//loops runs until either the user has run out of lives, or gameIsOverboolean is set to true
      
      System.out.print("Do you want to guess another word?(Yes or No) ");//User can choose to play again or not
      playAgain = " ";
      playAgain = sc.next();
    }while((playAgain.equalsIgnoreCase("Yes")));
    
  
  }
}


class Game
{
  private String word;

  Game()
  {
    word = null;
  }
  Game(String w)
  {
    this.word = w;
  }



/*
  The method wordFound determines if the user has guessed all the letters yet or not.
  //When thee user guesses will make swaps within the arrays, so when they have guessed
  enough to have found all the letters, this method should run true
*/
  public boolean wordFound(char [] notGuessedLetters)
          {
            int lettersGuessed = 0;//using this variable it can be found wether or not the user guessed the word
            for(int x = 0; x<notGuessedLetters.length;x++ )//The entire array is scanned to see if the array is done  
            {
              if(notGuessedLetters[x] == '_')
              {
                lettersGuessed++;
              }
            }
            if(lettersGuessed == notGuessedLetters.length)
            {
              return true;
            }
            else{
              return false;
            }
          }

  /*
    This method is used to calculate a bonus score, based on how many lives left
  */
  public int calcScore(int lives)
  {
    switch(lives)
    {
      case 6: 
      return 10;

      case 5:
      return 7;

      case 4:
      return 5;

      case 3:
      return 3;

      case 2: 
      return 2;

      case 1:
      return 1;

      default:
      return 0;
    }
  }

  /*
    This method is used to count how many of a letter is in a word.
    This is helpful for scores
  */
  public int letterIsInWord(char[] notGuessed, char letter)
  {
     int count = 0;
      for(int x = 0; x < notGuessed.length;x++)
      {
        if(letter == notGuessed[x] )
        {
          count++;
        }
        
      }
      
  return count;
  }

  /*
    When a letter is found by the user, the letter and the blank are swapped
  */
  public void letterSwitch(char[] notGuessed,char[] guessed, int index)
  {
    char temp;
    temp = notGuessed[index];
    notGuessed[index] = guessed[index];
    guessed[index]= temp;
  }
}

import java.util.Random;
class Words
{

  private String[] EasyWords = {"cat","male","Acid","blue","first","clean","clear","long","sad","safe","loud","dirty","deep","dry","soft",  "small","tall","true","wise","wide"};
  private String[] MediumWords = {"ability","abortion","disagree","above","absence","abuse","academic","accident","accuse","achieve","invest","acquire","enter","actor","holiday",  "ignore","figure","affect","butter","certain"};
  private String[] HardWords = {"weird","accommodate","handkerchief","indict","cemetery","conscience","playwright","embarrass","millennium","pharaoh","liaison","convalesce","supersede","pharaoh","liaison", "convalesce","supersede ","Caribbean","maintenance","pronunciation"};
  private String[] ImpossibleWords = {"czechoslovakia","connecticut","euclidean","australia","february","kwanzaa","parmesan","Presbyterian","teutonic","tuesday","wednesday","abandon","abyss","abysmal","abbreviate",  "absorbent","acknowledgment","accommodate","advantageous","aggrandize"};
  Words()
  {

  }

  //This method is what determines the word the user will need to guess depending on the challenge level they pick
  public String pickWord(int difficulty)
  {
    Random ran = new Random();    
    String word = null;
    int numWord = ran.nextInt(20);
    switch(difficulty)
    {
      case 1:
      word = EasyWords[numWord];
      break;
      case 2:
      word = MediumWords[numWord];
      case 3:
      word = HardWords[numWord];
      break;
      case 4:
      word = ImpossibleWords[numWord];
      break;
      default:
      break;
    }
    return word;
  }
}
