# java-2
Enter a Roman Number as input and convert it to an integer. (ex IX = 9)

import java.util.*;

public class RomanToInteger {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a Roman numeral: ");
        String roman = scanner.next();
        System.out.println("Integer: " + romanToInt(roman));
    }

    static int romanToInt(String s) {
        Map<Character, Integer> map = Map.of(
            'I', 1, 'V', 5, 'X', 10, 'L', 50, 'C', 100, 'D', 500, 'M', 1000
        );
        int total = 0;
        int prev = 0;
        for (char c : s.toCharArray()) {
            int value = map.get(c);
            total += value > prev ? value - 2 * prev : value;
            prev = value;
        }
        return total;
    }
}
