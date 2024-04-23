using System;
using System.Threading;

namespace TicTacToe
{
    class Program
    {
        static char[] arr = { '0', '1', '2', '3', '4', '5', '6', '7', '8', '9' };
        static int player = 1;
        static int choice;
        static int flag = 0;

        static void Main(string[] args)
        {
            do
            {
                Console.Clear();
                Console.WriteLine("Player 1: X and Player 2: O\n");

                if (player % 2 == 0)
                    Console.WriteLine("Player 2's Turn");
                else
                    Console.WriteLine("Player 1's Turn");

                Console.WriteLine("\n");
                DisplayBoard();
                choice = int.Parse(Console.ReadLine());

                if (arr[choice] != 'X' && arr[choice] != 'O')
                {
                    if (player % 2 == 0)
                        arr[choice] = 'O';
                    else
                        arr[choice] = 'X';

                    player++;
                }
                else
                {
                    Console.WriteLine($"Sorry, position {choice} is already marked with {arr[choice]}");
                    Console.WriteLine("Please wait 2 seconds. The board is loading again...");
                    Thread.Sleep(2000);
                }

                flag = CheckWin();
            } while (flag != 1 && flag != -1);

            Console.Clear();
            DisplayBoard();

            if (flag == 1)
                Console.WriteLine($"Player {(player % 2) + 1} has won!");
            else
                Console.WriteLine("It's a draw!");

            Console.ReadLine();
        }

        static void DisplayBoard()
        {
            Console.WriteLine(" | | ");
            Console.WriteLine($" {arr[1]} | {arr[2]} | {arr[3]}");
            Console.WriteLine("_____|_____|_____");
            Console.WriteLine(" | | ");
            Console.WriteLine($" {arr[4]} | {arr[5]} | {arr[6]}");
            Console.WriteLine("_____|_____|_____");
            Console.WriteLine(" | | ");
            Console.WriteLine($" {arr[7]} | {arr[8]} | {arr[9]}");
            Console.WriteLine(" | | ");
        }

        static int CheckWin()
        {
            return 0;
        }
    }
}
