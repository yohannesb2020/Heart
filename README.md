using System;
using System.IO;
public static class GlobalMembersHEART
{

    public static StreamWriter sw;
    public static int scnt;
    public static int scale;
    public static char[] charBuf = new char[512]; /* longer str makes it possible to write all over the heart */
    public static char[] charf = new char[20];
    public static string fname = new string(charf);
    public static string str = new string(charBuf);

    public static void prtch()
    {
        int no;
        for (no = 0; no < scale; no++)
        {
            Console.Write("{0}", str[scnt]);
            sw.Write("{0}", str[scnt]);
            scnt++;
            if (scnt == str.Length)
                scnt = 0;
        }
    }
    public static void prtspc()
    {
        int no;
        for (no = 0; no < scale; no++)
        {
            Console.Write(" ");
            sw.Write(" ");
        }
    }
    internal static void Main()
    {
        //System.IO.FileStream fopen; 
        int[] a = new int[21];
        int[] b = new int[21];
        int cnt;
        int li;
        int scl;
        int foo;
        string scales = new string(new char[4]);
        for (cnt = 0; cnt < 20; cnt++)
            a[cnt] = 1;
        a[1] = 9;
        b[1] = 20;
        a[2] = 6;
        b[2] = 24;
        a[3] = 4;
        b[3] = 27;
        a[4] = 3;
        b[4] = 28;
        a[5] = 2;
        b[5] = 29;
        b[6] = 29;
        b[7] = 29;
        b[8] = 28;
        b[9] = 28;
        b[10] = 26;
        b[11] = 24;
        b[12] = 22;
        b[13] = 20;
        b[14] = 18;
        b[15] = 16;
        b[16] = 14;
        b[17] = 11;
        b[18] = 7;
        b[19] = 2;
        Console.Write("Heart v1.4 written by Barnabas A. Yohannes. \n\n");
        Console.Write("text: ");
        str = Console.ReadLine();
        Console.Write("file: ");
        fname = Console.ReadLine();
        fname = fname + ".txt";
        sw = new StreamWriter(fname);

        scale = 0;
        while (scale < 1 || scale > 3)
        {
            Console.Write("scale [1-3]: ");
            scales = Console.ReadLine();
            scale = Convert.ToInt32(scales);
        }
        //if ((fp = fopen(fname, "w")) == null)
        //{
        //    Console.Write("could not open file.\n");
        //    Console.Read();
        //}
        Console.Write("\n\n");
        li = 1;
        scnt = 0;
        for (li = 1; li <= 19; li++)
        {
            for (scl = 0; scl < scale; scl++)
            {
                for (cnt = 0; cnt < 30 - b[li]; cnt++)
                    prtspc();
                for (cnt = 0; cnt < b[li] - a[li]; cnt++)
                    prtch();    
                foo = a[li] + a[li];
                while (foo > 2)
                {
                    foo--;
                    prtspc();
                }
                for (cnt = 0; cnt < b[li] - a[li]; cnt++)
                    prtch();
                Console.Write("\n");
                sw.WriteLine("  ");
                //System.Diagnostics.Debug.WriteLine(fp, "\n");
            }
        }
        //if (fclose(fp)) //suggested by Paal D. Ekran
        //    Console.Write("file close error.");
        sw.Close();
        Console.Read();
    }
}
