# PasswordGenerator
Code generates 8 lengths password
package com.javarush.task.task32.task3204;



import java.io.*;

import java.util.*;

/* 
Генератор паролей
*/

public class Solution {
    public static void main(String[] args) throws IOException {
      ByteArrayOutputStream password = getPassword();
      System.out.println(password);

    }

    public static ByteArrayOutputStream getPassword() {
        int a = 48;
        int b = 65;
        int c = 97;

        Random random = new Random();

        char [] charsArray = new char[8];

        for (int i = 0; i < charsArray.length; i++) {
            if (i <= 2 ){
                charsArray[i] = (char) (a + random.nextInt(10));
            } else if (i < 5){
                charsArray[i] = (char) (b + random.nextInt(26));
            } else {
                charsArray[i] = (char) (c + random.nextInt(26));
            }
        }

        ArrayList <Character> list = new ArrayList<>();

        for (char item : charsArray) {
            list.add(item);
        }

        Collections.shuffle(list);

        ByteArrayOutputStream byteArrayOutputStream = new ByteArrayOutputStream();

        for (Character value : list) {
            byteArrayOutputStream.write(value);
        }

        return byteArrayOutputStream;
    }
}
