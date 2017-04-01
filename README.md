# GCprework

package com.company;
import java.util.Date;
import java.util.Scanner;

public class daysBtwnDates {
    public int numberOfDays(String fromDate,String toDate)
    {
        java.util.Calendar cal1 = new java.util.GregorianCalendar();
        java.util.Calendar cal2 = new java.util.GregorianCalendar();

        //split year, month and days from the date using StringBuffer.
        StringBuffer sBuffer = new StringBuffer(fromDate);
        String yearFrom = sBuffer.substring(6,10);
        String monFrom = sBuffer.substring(0,2);
        String ddFrom = sBuffer.substring(3,5);
        int intYearFrom = Integer.parseInt(yearFrom);
        int intMonFrom = Integer.parseInt(monFrom);
        int intDdFrom = Integer.parseInt(ddFrom);

        // set the fromDate in java.util.Calendar
        cal1.set(intYearFrom, intMonFrom, intDdFrom);

        //split year, month and days from the date using StringBuffer.
        StringBuffer sBuffer1 = new StringBuffer(toDate);
        String yearTo = sBuffer1.substring(6,10);
        String monTo = sBuffer1.substring(0,2);
        String ddTo = sBuffer1.substring(3,5);
        int intYearTo = Integer.parseInt(yearTo);
        int intMonTo = Integer.parseInt(monTo);
        int intDdTo = Integer.parseInt(ddTo);

        // set the toDate in java.util.Calendar
        cal2.set(intYearTo, intMonTo, intDdTo);

        //call method daysBetween to get the number of days between two dates
        int days = daysBetween(cal1.getTime(),cal2.getTime());
        return days;
    }

    //This method is called by the above method numberOfDays
    public int daysBetween(Date d1, Date d2)
    {
        return (int)( (d2.getTime() - d1.getTime()) / (1000 * 60 * 60 * 24));
    }

    public static void main(String args[]){
        daysBtwnDates obj= new daysBtwnDates();

        String fromDate, toDate;

        System.out.println("Input your beginning date in mm-dd-yyyy format: ");
        Scanner in = new Scanner(System.in);
        fromDate = in.next();

        System.out.println("Input your ending date in mm-dd-yyyy format: ");
        toDate = in.next();

        int num= obj.numberOfDays(fromDate, toDate);
        System.out.println("Number of days between the two dates are: "+num);
    }
}
