using System;
using System.Linq;
using System.Text;

class Program
{
    static void Main()
    {
        Console.WriteLine("Enter the input line:");
        string input = Console.ReadLine();

        string reversedLine = ReverseWords(input);
        Console.WriteLine("Reversed line: " + reversedLine);
    }

    static string ReverseWords(string input)
    {
        StringBuilder result = new StringBuilder();
        char[] delimiters = { ' ' };

        string[] words = input.Split(delimiters, StringSplitOptions.None);

        foreach (string word in words)
        {
            string reversedWord = ReverseAlphabeticChars(word);
            result.Append(reversedWord).Append(' ');
        }

        return result.ToString().TrimEnd();
    }

    static string ReverseAlphabeticChars(string word)
    {
        char[] characters = word.ToCharArray();
        int start = 0;
        int end = characters.Length - 1;

        while (start < end)
        {
            if (!char.IsLetter(characters[start]))
            {
                start++;
            }
            else if (!char.IsLetter(characters[end]))
            {
                end--;
            }
            else
            {
                char temp = characters[start];
                characters[start] = characters[end];
                characters[end] = temp;
                start++;
                end--;
            }
        }

        return new string(characters);
    }
}
