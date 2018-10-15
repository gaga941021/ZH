package andinak

import java.io.*;
import java.io.FileNotFoundException;
import java.util.*;
import java.util.logging.Level;
import java.util.logging.Logger;


class Gyumolcs {
    //Attributumok
    String nev;
    int energia;
    int kcal;
    double feherje;
    double sav;
    double szenhidrat;
    double rost;
    
}

public class Gyak_5 {
    public static void readFile(File f, ArrayList<Gyumolcs> gyum) {
        
        try {
            Scanner sc = new Scanner(f, "ISO-8859-2");
            //Ha van fejlec
            //sc.nextLine();
            while(sc.hasNextLine()) {
                String sor = sc.nextLine();
                String[] adatok = sor.split(";");
                //Irja ki az adatok tomb 0. elemet
                //System.out.println(adatok[0]);  
                
                Gyumolcs gy = new Gyumolcs();
                gy.nev = adatok[0];
                gy.energia = Integer.parseInt(adatok[1]);
                gy.kcal = Integer.parseInt(adatok[2]);
                gy.feherje = Double.parseDouble(adatok[3]);
                gy.sav = Double.parseDouble(adatok[4]);
                gy.szenhidrat = Double.parseDouble(adatok[5]);
                gy.rost = Double.parseDouble(adatok[6]);
                
                //Az elobb osszegyujtott adatok bevitele a gyumolcskosarba
                gyum.add(gy);
                        
                        
                //Ha ellenorizni akarom
                //System.out.println(gy.energia);
            }
        } catch (FileNotFoundException ex) {
            System.out.println("Nincs meg a fajl");
        }
        
    }
    public static void f1(ArrayList<Gyumolcs> gy, String name, int mennyiseg) {
        //Egyik modszer:
        for (Gyumolcs item : gy) {
        //Masik modszer, fori modszer:
        //for (int i = 0; i < gy.size(); i++) {
            //System.out.println(item.nev);
            if(item.nev.equals(name)) {
                System.out.println(item.kcal * mennyiseg/100);
            }
        }
    }
    public static ArrayList<String> f2(ArrayList<Gyumolcs> gy) {
        //Valtozo letrehozasa
        ArrayList<String> out = new ArrayList<>();
        
        //Vegig megyek az osszes elemen
        for (int i = 0; i < gy.size(); i++) {
            //System.out.println(gy.get(i).szenhidrat);
            
            //Ha nagyobb, mint 10
            if(gy.get(i).szenhidrat > 10) {
                //Hozzaadom a listahoz
                out.add(gy.get(i).nev);
                
            }
        }
        return out;
    }
            
    public static void main(String[] args) {
        //Ez fog lefuti
        
        //Fajlbeolvasas
        ArrayList<Gyumolcs> gyumolcskosar = new ArrayList<>();
        //"K:\_INFORMATIKA\FausztT\filekezeles\gyumolcs.csv"
        File f = new File("K:\\_INFORMATIKA\\FausztT\\filekezeles\\gyumolcs.csv");
        readFile(f, gyumolcskosar);
        
        
        //f1(gyumolcskosar, "Alma", 500);
        f2(gyumolcskosar);
   
        //Ellenorzes
        //System.out.println(gyumolcskosar.size());
        
        System.out.println(f2(gyumolcskosar));
    }
}

