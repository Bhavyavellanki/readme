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
