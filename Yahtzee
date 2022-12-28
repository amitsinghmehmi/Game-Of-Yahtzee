import java.io.File;
import java.io.IOException;
import javax.sound.sampled.AudioInputStream;
import javax.sound.sampled.AudioSystem;
import javax.sound.sampled.Clip;
import javax.sound.sampled.LineUnavailableException;
import javax.sound.sampled.UnsupportedAudioFileException;
import javax.swing.ImageIcon;
import javax.swing.JOptionPane;

/**
 * 
 */

/**
 * @author Amit Singh Mehmi
 * Date: March 12th, 2022
 * Description: This program will execute the game of Yahtzee. Prizes are Yahtzee, full house, small straight,
 * 				large straight, four of a kind and three of a kind 
 *
 */
public class Yahtzee {

	/**
	 * @param args
	 * @throws LineUnavailableException 
	 * @throws IOException 
	 * @throws UnsupportedAudioFileException 
	 */
	public static void main(String[] args) throws LineUnavailableException, IOException, UnsupportedAudioFileException {

		// Setting up audio learned from: https://www.youtube.com/watch?v=SyZQVJiARTQ
		File file = new File("Winner Gagnant!.wav");
		AudioInputStream audioStream = AudioSystem.getAudioInputStream(file);
		Clip clip = AudioSystem.getClip();
		clip.open(audioStream);

		// Declaring and initializing image icons 
		ImageIcon resultIcon = new ImageIcon("resultIcon.png");
		ImageIcon rollAgainIcon = new ImageIcon("rollAgainIcon.png");
		ImageIcon yahtzeeIcon = new ImageIcon("yahtzeeIcon.png");

		// Declaring integers
		int userMoney, continuation, userMoneyIntial;
		
		// String
		String gainlossStr = null;

		// Declaring and initializing arrays
		int dieCount[]; 
		dieCount = new int [6];
		int dieValues[];
		dieValues = new int [5];

		// Welcome message
		JOptionPane.showMessageDialog(null, "Welcome to the game of Yahtzee!", "YAHTZEE!", JOptionPane.INFORMATION_MESSAGE, yahtzeeIcon);

		// Asking for user's betting amount
		userMoneyIntial = Integer.parseInt(JOptionPane.showInputDialog(null, "Please enter betting amount to start (>=$10): ", "BETTING AMOUNT", JOptionPane.INFORMATION_MESSAGE));

		// Loop until user enters a bet greater than or equal to $10
		while (userMoneyIntial < 10) {
			userMoneyIntial = Integer.parseInt(JOptionPane.showInputDialog(null, "Betting amount must be >= $10 to start: ", "BETTING AMOUNT", JOptionPane.INFORMATION_MESSAGE));
		}

		// Storing user's initial winning money as zero and taking away 10 for starting the game
		userMoney = userMoneyIntial - 10;
		
		
		// Looping until user runs out of money or does not want to continue
		while (userMoney >= 0) {
			
			// Declaring variables 
			int numOnes=0, numTwos=0, numThrees=0, numFours=0, numFives=0, numSixes=0;
			String result = "NO PRIZE";

			// Random dice roll
			for (int i = 0 ; i < 5 ; i++) {
				dieValues[i] = (int) (Math.random() * 6 + 1);
			}
			

			// Counting number of occurrences and storing into a variable   
			for (int i = 0 ; i < 5 ; i++) {
				if (dieValues[i] == 1) {
					numOnes++;
				}
				else if (dieValues[i] == 2) {
					numTwos++;
				}
				else if (dieValues[i] == 3) {
					numThrees++;
				}
				else if (dieValues[i] == 4) {
					numFours++;
				}
				else if (dieValues[i] == 5) {
					numFives++;
				}
				else {
					numSixes++;
				}
			}

			// Putting Occurrences into an array 
			dieCount[0] = numOnes;
			dieCount[1] = numTwos;
			dieCount[2] = numThrees;
			dieCount[3] = numFours;
			dieCount[4] = numFives;
			dieCount[5] = numSixes;

			// Deciding if user won Yahtzee, three straight, full house etc. 

			// Yahtzee
			if(dieValues[0] == 1 && dieValues[1] == 1 && dieValues[2] == 1 && dieValues[3] == 1 && dieValues[4] == 1||	// 11111
			   dieValues[0] == 2 && dieValues[1] == 2 && dieValues[2] == 2 && dieValues[3] == 2 && dieValues[4] == 2||	// 22222	
			   dieValues[0] == 3 && dieValues[1] == 3 && dieValues[2] == 3 && dieValues[3] == 3 && dieValues[4] == 3||	// 33333
			   dieValues[0] == 4 && dieValues[1] == 4 && dieValues[2] == 4 && dieValues[3] == 4 && dieValues[4] == 4||	// 44444	
			   dieValues[0] == 5 && dieValues[1] == 5 && dieValues[2] == 5 && dieValues[3] == 5 && dieValues[4] == 5||	// 55555
			   dieValues[0] == 6 && dieValues[1] == 6 && dieValues[2] == 6 && dieValues[3] == 6 && dieValues[4] == 6	// 66666
					) {
					result = "YAHTZEE!";
					userMoney = userMoney + 1000;
			}

			// Large straight 
			else if (dieValues[0] == 1 && dieValues[1] == 2 && dieValues[2] == 3 && dieValues[3] == 4 && dieValues[4] == 5|| 	// 12345
				dieValues[0] == 2 && dieValues[1] == 3 && dieValues[2] == 4 && dieValues[3] == 5 && dieValues[4] == 6 ) {		// 23456
				result = "LARGE STRAIGHT";
				userMoney = userMoney + 250;
			}

			// Small straight 
			else if (dieValues[0] == 1 && dieValues[1] == 2 && dieValues[2] == 3 && dieValues[3] == 4 ||	// If number is 1234X
					dieValues[0] == 2 && dieValues[1] == 3 && dieValues[2] == 4 && dieValues[3] == 5  ||	// 2345X
					dieValues[0] == 3 && dieValues[1] == 4 && dieValues[2] == 5 && dieValues[3] == 6  		// 3456X
					) {	
				result = "SMALL STRAIGHT";
				userMoney = userMoney + 100;
			}

			// Four of a kind
			else if (dieValues[0] == 1 && dieValues[1] == 1 && dieValues[2] == 1  && dieValues[3] == 1 || 	// 1111X
					 dieValues[0] == 2 && dieValues[1] == 2 && dieValues[2] == 2  && dieValues[3] == 2 || 	// 2222X
					 dieValues[0] == 3 && dieValues[1] == 3 && dieValues[2] == 3  && dieValues[3] == 3 || 	// 3333X
					 dieValues[0] == 4 && dieValues[1] == 4 && dieValues[2] == 4  && dieValues[3] == 4 || 	// 4444X
					 dieValues[0] == 5 && dieValues[1] == 5 && dieValues[2] == 5  && dieValues[3] == 5 ||	// 5555X
					 dieValues[0] == 6 && dieValues[1] == 6 && dieValues[2] == 6  && dieValues[3] == 6  	// 6666X
					) {
				result = "FOUR OF A KIND";
				userMoney = userMoney + 50;
			}


			// Full house
			else if (dieValues[0] == 1 && dieValues[1] == 1 && dieValues[2] == 1  && dieValues[3] == 2 && dieValues[4] == 2 ||	// 11122	
					 dieValues[0] == 1 && dieValues[1] == 1 && dieValues[2] == 1  && dieValues[3] == 3 && dieValues[4] == 3 ||	// 11133
					 dieValues[0] == 1 && dieValues[1] == 1 && dieValues[2] == 1  && dieValues[3] == 4 && dieValues[4] == 4 ||	// 11144
					 dieValues[0] == 1 && dieValues[1] == 1 && dieValues[2] == 1  && dieValues[3] == 5 && dieValues[4] == 5 ||	// 11155
					 dieValues[0] == 1 && dieValues[1] == 1 && dieValues[2] == 1  && dieValues[3] == 6 && dieValues[4] == 6 ||	// 11166 
					 
					 dieValues[0] == 2 && dieValues[1] == 2 && dieValues[2] == 2  && dieValues[3] == 1 && dieValues[4] == 1 ||	// 22211
					 dieValues[0] == 2 && dieValues[1] == 2 && dieValues[2] == 2  && dieValues[3] == 3 && dieValues[4] == 3 ||	// 22233
					 dieValues[0] == 2 && dieValues[1] == 2 && dieValues[2] == 2  && dieValues[3] == 4 && dieValues[4] == 4 ||	// 22244
					 dieValues[0] == 2 && dieValues[1] == 2 && dieValues[2] == 2  && dieValues[3] == 5 && dieValues[4] == 5 ||	// 22255
					 dieValues[0] == 2 && dieValues[1] == 2 && dieValues[2] == 2  && dieValues[3] == 6 && dieValues[4] == 6 ||	// 22266
					 
					 dieValues[0] == 3 && dieValues[1] == 3 && dieValues[2] == 3  && dieValues[3] == 1 && dieValues[4] == 1 ||	// 33311
					 dieValues[0] == 3 && dieValues[1] == 3 && dieValues[2] == 3  && dieValues[3] == 2 && dieValues[4] == 2 ||	// 33322
					 dieValues[0] == 3 && dieValues[1] == 3 && dieValues[2] == 3  && dieValues[3] == 4 && dieValues[4] == 4 ||	// 33344
					 dieValues[0] == 3 && dieValues[1] == 3 && dieValues[2] == 3  && dieValues[3] == 5 && dieValues[4] == 5 ||	// 33355
					 dieValues[0] == 3 && dieValues[1] == 3 && dieValues[2] == 3  && dieValues[3] == 6 && dieValues[4] == 6 ||	// 33366
					 
					 dieValues[0] == 4 && dieValues[1] == 4 && dieValues[2] == 4  && dieValues[3] == 1 && dieValues[4] == 1 ||	// 44411
					 dieValues[0] == 4 && dieValues[1] == 4 && dieValues[2] == 4  && dieValues[3] == 2 && dieValues[4] == 2 ||	// 44422
					 dieValues[0] == 4 && dieValues[1] == 4 && dieValues[2] == 4  && dieValues[3] == 3 && dieValues[4] == 3 ||	// 44433
					 dieValues[0] == 4 && dieValues[1] == 4 && dieValues[2] == 4  && dieValues[3] == 5 && dieValues[4] == 5 ||	// 44455
					 dieValues[0] == 4 && dieValues[1] == 4 && dieValues[2] == 4  && dieValues[3] == 6 && dieValues[4] == 6 ||	// 44466
					 
					 dieValues[0] == 5 && dieValues[1] == 5 && dieValues[2] == 5  && dieValues[3] == 1 && dieValues[4] == 1 ||	// 55511
					 dieValues[0] == 5 && dieValues[1] == 5 && dieValues[2] == 5  && dieValues[3] == 2 && dieValues[4] == 2 ||	// 55522
					 dieValues[0] == 5 && dieValues[1] == 5 && dieValues[2] == 5  && dieValues[3] == 3 && dieValues[4] == 3 ||	// 55533
					 dieValues[0] == 5 && dieValues[1] == 5 && dieValues[2] == 5  && dieValues[3] == 4 && dieValues[4] == 4 ||	// 55544
					 dieValues[0] == 5 && dieValues[1] == 5 && dieValues[2] == 5  && dieValues[3] == 6 && dieValues[4] == 6 ||	// 55566

					 dieValues[0] == 6 && dieValues[1] == 6 && dieValues[2] == 6  && dieValues[3] == 1 && dieValues[4] == 1 ||	// 66611
					 dieValues[0] == 6 && dieValues[1] == 6 && dieValues[2] == 6  && dieValues[3] == 2 && dieValues[4] == 2 ||	// 66622
					 dieValues[0] == 6 && dieValues[1] == 6 && dieValues[2] == 6  && dieValues[3] == 3 && dieValues[4] == 3 ||	// 66633
					 dieValues[0] == 6 && dieValues[1] == 6 && dieValues[2] == 6  && dieValues[3] == 4 && dieValues[4] == 4 ||	// 66644
					 dieValues[0] == 6 && dieValues[1] == 6 && dieValues[2] == 6  && dieValues[3] == 5 && dieValues[4] == 5 	// 66655
					) {	
				result = "FULL HOUSE";
				userMoney = userMoney + 30;
			}

			// Three of a kind
			else if (dieValues[0] == 1 && dieValues[1] == 1 && dieValues[2] == 1 ||	// 111XX
					 dieValues[0] == 2 && dieValues[1] == 2 && dieValues[2] == 2 ||	// 222XX
					 dieValues[0] == 3 && dieValues[1] == 3 && dieValues[2] == 3 ||	// 333XX
					 dieValues[0] == 4 && dieValues[1] == 4 && dieValues[2] == 4 ||	// 444XX
					 dieValues[0] == 5 && dieValues[1] == 5 && dieValues[2] == 5 ||	// 555XX
					 dieValues[0] == 6 && dieValues[1] == 6 && dieValues[2] == 6 	// 666XX
					) {
				result = "THREE OF A KIND";
				userMoney = userMoney + 20;
			}
			
			// gain loss
						if (userMoney < userMoneyIntial) {
							gainlossStr = "You lost: $" + (userMoneyIntial - userMoney);
						}
						else {
							gainlossStr = "You gained: $" + (userMoney - userMoneyIntial);
						}


			// If user wins a prize play audio
			if (result == "THREE OF A KIND" || result == "FOUR OF A KIND" || result == "FULL HOUSE" || 
					result == "SMALL STRAIGHT" || result == "LARGE STRAIHGT"|| result == "YAHTZEE") {
				clip.setMicrosecondPosition(0);	// Resets audio to beginning 
				clip.start();					// Plays audio
			}

			// Output values of dice roll and result 
			JOptionPane.showMessageDialog(null, "| Dice # |  1  |  2  |  3  |  4  |  5  |\n"
					+ "| Value  |  " + dieValues[0] + "  |  " + dieValues[1] + "  |  " + dieValues[2] + "  |  " + dieValues[3] + "  |  " + dieValues[4] + "  | " + 
					"\n \nNumber of Ones: " + dieCount[0] +"\nNumber of Twos: " + dieCount[1] + "\nNumber of Threes: " + dieCount[2] + "\nNumber of Fours: " + dieCount[3] + 
					"\nNumber of Fives: " + dieCount[4] + "\nNumber of Sixes: " + dieCount[5] +
					"\n \nResult: " + result + "\nMoney remaining: $" + userMoney + "\n" + gainlossStr,
					"RESULT", JOptionPane.INFORMATION_MESSAGE, resultIcon);

			// If enters $10 and loses, it stops the game
			if (userMoney == 0) {
				break;
			}
			else {
				clip.stop();
				continuation = JOptionPane.showConfirmDialog(null, "Would you like to play again? (-$10)", "PLAY AGAIN?",
						JOptionPane.YES_NO_OPTION, JOptionPane.QUESTION_MESSAGE, rollAgainIcon);

				// End game if user says no
				if (continuation == JOptionPane.NO_OPTION) {
					break;
				}

				// Taking away $10 from user's money if they want to continue 
				userMoney = userMoney - 10;

			}
		}	// End of while loop

		// Thank you message with money gained/loss 
		JOptionPane.showMessageDialog(null, "Thank you for playing Yahtzee!\n" + gainlossStr, "YAHTZEE!", JOptionPane.INFORMATION_MESSAGE, yahtzeeIcon);

	} // End of main method


}	// End of class 
