public class Question1 {
public static void findMinMaxChar (String str) {
Map<Character, Integer> charCountMap = new HashMap<>();
for (char ch: str.toCharArray()) {
charCountMap.put(ch, charCountMap.getOrDefault(ch, 0) + 1);
}
char minChar = ', maxChar ';
int min = Integer.MAX_VALUE, max = Integer.MIN_VALUE;
for (Map. Entry<Character, Integer> entry charCountMap.entrySet()) {
if (entry.getValue() < min) {
min = entry.getValue();
minChar = entry.getKey();
}
if(entry.getValue() > max) {
max = entry.getValue();
maxChar = entry.getKey();
}
}
System.out.println("Minimum occuring character: " + minChar + ", Count: " + min + ")");
System.out.println("Maximum occuring character : + maxChar + ", Count: + max + ")");
}

public class CharFrequencyAnalyzer {
    public static void main(String[] args) {
        String input = "Hello World, how are you doing today?";
        findMaxMinOccurringChar(input);
    }

    public static void findMaxMinOccurringChar(String str) {
        // Remove spaces and convert to lowercase for consistency
        str = str.replaceAll("\\s", "").toLowerCase();
        
        // If the string is empty, return
        if (str.length() == 0) {
            System.out.println("Input string is empty");
            return;
        }
        
        // Create an array to store frequency of each character (ASCII values)
        int[] freq = new int[256];
        
        // Count the frequency of each character
        for (int i = 0; i < str.length(); i++) {
            freq[str.charAt(i)]++;
        }
        
        char maxChar = '\0';
        char minChar = '\0';
        int maxFreq = 0;
        int minFreq = Integer.MAX_VALUE;
        
        // Find max and min occurring characters
        for (int i = 0; i < 256; i++) {
            if (freq[i] > 0) { // Only consider characters that occur at least once
                if (freq[i] > maxFreq) {
                    maxFreq = freq[i];
                    maxChar = (char) i;
                }
                
                if (freq[i] < minFreq) {
                    minFreq = freq[i];
                    minChar = (char) i;
                }
            }
        }
        
        System.out.println("Maximum occurring character: '" + maxChar + "' - " + maxFreq + " times");
        System.out.println("Minimum occurring character: '" + minChar + "' - " + minFreq + " times");
    }
}
