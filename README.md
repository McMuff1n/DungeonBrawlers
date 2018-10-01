using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace DungeonBrawlers
{
    class Program
    {
        static string Name;
        static bool Gender; //false is female, true is male

        static void Main(string[] args)
        {
            Console.CursorVisible = false;
            greet();
        }

        static void greet()
        {
            Console.Write("Write your character name here: ");
            Name = Console.ReadLine(); //Puts the username in a static variable
            Console.Clear();
            Console.Write("Choose one of the following genders\n\n  Female\n  Male");
            int genderSelectResult = selector(2, 0, 3, 2) - 2; //0 is female, 1 is male
            if (genderSelectResult == 0)
                Gender = false;
            else if (genderSelectResult == 1)
                Gender = true;
        }

        static int selector(int yPos, int xPos, int yMax, int yMin) //This will be the base of all choices, a selector that uses the up- and downarrows for navigation
        {
            Console.SetCursorPosition(xPos, yPos);
            for (;;)
            {
                Console.Write("\b\b ");
                Console.SetCursorPosition(xPos, yPos);
                Console.Write(">");
                ConsoleKeyInfo info = Console.ReadKey();
                if (info.Key == ConsoleKey.DownArrow)
                {
                    if (yPos >= yMax)
                        yPos = yMin;
                    else
                        yPos++;
                }
                else if (info.Key == ConsoleKey.UpArrow)
                {
                    if (yPos <= yMin)
                        yPos = yMax;
                    else
                        yPos--;
                }
                else if (info.Key == ConsoleKey.Enter)
                    return yPos;
            }
        }
    }
}
