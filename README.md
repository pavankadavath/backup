public class Main
{
    public static void main(String[] args) {
        String text = "Hello world";
        int key = 2;

        String encryptedText = encrypt(text, key);
        System.out.println("Encrypted: " + encryptedText);

        String decryptedText = decrypt(encryptedText, key);
        System.out.println("Decrypted: " + decryptedText);
    }

    static String encrypt(String text, int key) {
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < text.length(); i++) {
            char ch = text.charAt(i);
            if (Character.isUpperCase(ch)) {
                char x = (char) (((ch + key - 65) % 26) + 65);
                sb.append(x);
            } else if (Character.isLowerCase(ch)) {
                char y = (char) (((ch + key - 97) % 26) + 97);
                sb.append(y);
            } else {
                sb.append(ch);
            }
        }
        return sb.toString();
    }

    static String decrypt(String text, int key) {
        return encrypt(text, 26 - key); 
    }
}

import java.util.Scanner;

public class Main {
    private static final String ALPHABET = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String key = "QWERTYUIOPASDFGHJKLZXCVBNM";

        String plaintext = "Hellow World";

        String encryptedText = encrypt(plaintext, key);
        System.out.println("Encrypted text: " + encryptedText);

        String decryptedText = decrypt(encryptedText, key);
        System.out.println("Decrypted text: " + decryptedText);
    }

    public static String encrypt(String text, String key) {
        StringBuilder result = new StringBuilder();
        text = text.toUpperCase();

        for (char ch : text.toCharArray()) {
            if (Character.isLetter(ch)) {
                int index = ALPHABET.indexOf(ch);
                result.append(key.charAt(index));
            } else {
                result.append(ch); 
            }
        }
        return result.toString();
    }

    public static String decrypt(String text, String key) {
        StringBuilder result = new StringBuilder();
        text = text.toUpperCase();

        for (char ch : text.toCharArray()) {
            if (Character.isLetter(ch)) {
                int index = key.indexOf(ch);
                result.append(ALPHABET.charAt(index));
            } else {
                result.append(ch); 
            }
        }
        return result.toString();
    }

}


//Write a java program to implement the DES algorithm logic?

import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;
import javax.crypto.spec.SecretKeySpec;
import java.util.Base64;

public class Main {
    public static void main(String[] args) {
        try{
            
        SecretKey key =generateKey();

        String plaintext = "Hellow World";

        String encryptedText = encrypt(plaintext, key);
        System.out.println("Encrypted text: " + encryptedText);

        String decryptedText = decrypt(encryptedText, key);
        System.out.println("Decrypted text: " + decryptedText);
        }catch(Exception e){
            System.out.println("Failed to generate");
        }
    }
    public static SecretKey generateKey()throws Exception{
        KeyGenerator key=KeyGenerator.getInstance("DES");
        key.init(56);
        return key.generateKey();
    }
    public static String encrypt(String text, SecretKey key)throws Exception {
        Cipher cipher=Cipher.getInstance("DES");
        cipher.init(Cipher.ENCRYPT_MODE,key);
        byte []encryptbytes=cipher.doFinal(text.getBytes());
        return Base64.getEncoder().encodeToString(encryptbytes);
    }

    public static String decrypt(String text, SecretKey key) throws Exception{
        Cipher cipher=Cipher.getInstance("DES");
        cipher.init(Cipher.DECRYPT_MODE,key);
        byte []decryptbytes=cipher.doFinal(Base64.getDecoder().decode(text));
        return new String(decryptbytes);
        
    }
}



//Write a java program to implement the Blowfish algorithm logic?


import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;
import javax.crypto.spec.SecretKeySpec;
import java.util.Base64;

public class Main {
    public static void main(String[] args) {
        try{
            
        SecretKey key =generateKey(128);

        String plaintext = "Hellow World";

        String encryptedText = encrypt(plaintext, key);
        System.out.println("Encrypted text: " + encryptedText);

        String decryptedText = decrypt(encryptedText, key);
        System.out.println("Decrypted text: " + decryptedText);
        }catch(Exception e){
            System.out.println("Failed to generate");
        }
    }
    public static SecretKey generateKey(int size)throws Exception{
        KeyGenerator key=KeyGenerator.getInstance("Blowfish");
        key.init(size);
        return key.generateKey();
    }
    public static String encrypt(String text, SecretKey key)throws Exception {
        Cipher cipher=Cipher.getInstance("Blowfish");
        cipher.init(Cipher.ENCRYPT_MODE,key);
        byte []encryptbytes=cipher.doFinal(text.getBytes());
        return Base64.getEncoder().encodeToString(encryptbytes);
    }

    public static String decrypt(String text, SecretKey key) throws Exception{
        Cipher cipher=Cipher.getInstance("Blowfish");
        cipher.init(Cipher.DECRYPT_MODE,key);
        byte []decryptbytes=cipher.doFinal(Base64.getDecoder().decode(text));
        return new String(decryptbytes);
        
    }
}


//Write a java program to implement the Rijndael algorithm logic?

import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;
import javax.crypto.spec.SecretKeySpec;
import java.util.Base64;

public class Main {
    public static void main(String[] args) {
        try{
        SecretKey key =generateKey(128);
        String plaintext = "Hellow World";
        String encryptedText = encrypt(plaintext, key);
        System.out.println("Encrypted text: " + encryptedText);
        String decryptedText = decrypt(encryptedText, key);
        System.out.println("Decrypted text: " + decryptedText);
        }catch(Exception e){
            System.out.println("Failed to generate");
        }
    }
    public static SecretKey generateKey(int size)throws Exception{
        KeyGenerator key=KeyGenerator.getInstance("AES");
        key.init(size);
        return key.generateKey();
    }
    public static String encrypt(String text, SecretKey key)throws Exception {
        Cipher cipher=Cipher.getInstance("AES");
        cipher.init(Cipher.ENCRYPT_MODE,key);
        byte []encryptbytes=cipher.doFinal(text.getBytes());
        return Base64.getEncoder().encodeToString(encryptbytes);
    }

    public static String decrypt(String text, SecretKey key) throws Exception{
        Cipher cipher=Cipher.getInstance("AES");
        cipher.init(Cipher.DECRYPT_MODE,key);
        byte []decryptbytes=cipher.doFinal(Base64.getDecoder().decode(text));
        return new String(decryptbytes);
        
    }
}



//Write a java program to calculate the message digest of text using the SHA-1 algorithm?

import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;

public class Main {
    public static void main(String[] args) {
        String plaintext = "Hellow World";
        try{
            MessageDigest md=MessageDigest.getInstance("SHA-1");
            md.update(plaintext.getBytes());
            byte []digest=md.digest();
            StringBuilder sb=new StringBuilder();
            for(byte b:digest){
                sb.append(String.format("%02x",b));
            }
        System.out.println(sb.toString());
        }catch(NoSuchAlgorithmException e){
            System.out.println("Failed to generate");
        }
    }
    
}



//Write a java program to calculate the message digest of text using the MD5 algorithm?

import java.security.MessageDigest;
import java.security.NoSuchAlgorithmException;

public class Main {
    public static void main(String[] args) {
        String plaintext = "Hellow World";
        try{
            MessageDigest md=MessageDigest.getInstance("MD5");
            md.update(plaintext.getBytes());
            byte []digest=md.digest();
            StringBuilder sb=new StringBuilder();
            for(byte b:digest){
                sb.append(String.format("%02x",b));
            }
        System.out.println(sb.toString());
        }catch(NoSuchAlgorithmException e){
            System.out.println("Failed to generate");
        }
    }
    
}




