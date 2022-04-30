package com.company.locker;

import java.io.File;
import java.util.LinkedList;
import java.util.Scanner;

public class LockedMe 
{
	static final String projectpath="D:\\JAVA Project 1\\CompanyLockers\\Lockedme Project";
    static Scanner obj;

	public static void main(String[] args)
	{
		try (Scanner obj = new Scanner(System.in)) {
			int ch;
			displaymenu();
			System.out.println("\tEnter your choice");
			ch=Integer.parseInt(obj.nextLine());
			
			switch(ch)
			{
			case 1:getallfiles();
			break;
			case 2:createfiles();
			break;
			case 3:deletefiles();
			break;
			case 4:searchfiles();
			break;
			case 5:System.exit(0);
			default:System.out.println("Invalid Option");
			break;
			}
		}
		}
		
	public static void displaymenu()
	{
		System.out.println("\t*****************************************");
		System.out.println("\tWelcome to company Lockers -LockedMe.com");
		System.out.println("\tDeveloper Name: Adarsh Gopal Singh");
		System.out.println("\t*****************************************");
		System.out.println("\t1.Display All Files");
		System.out.println("\t2.Add Files to Existing Directory");
		System.out.println("\t3.Delete a File");
		System.out.println("\t4.Search a File");
		System.out.println("\t5.Exit");
		System.out.println("\t*****************************************");

		
		obj = new Scanner(System.in);
		obj.next();
		
	}
	public static void getallfiles()
	{
		new file(projectpath);
		File[] listoffiles=file.listfiles;
		if(listoffiles.length==0)
		System.out.println("No File exist in the directory");
		else
		{
			for(File l:listoffiles);
			{
				System.out.println(l.getName());
			}
		}
	}
	public static void createfiles()
	{
		try 
		{
			Scanner obj= new Scanner(System.in);
			String fileName;
			System.out.println("Enter File Name:");
			fileName=obj.nextLine();
			
			System.out.println("Enter how many lines you want to add in File:");
			int linesCount = Integer.parseInt(obj.nextLine());
			
			Filewriter fw= new Filewriter(projectpath+"\\"+fileName);
			
			for(int i=1;i<=linesCount;i++)
			{
			System.out.println("Enter the file content");
			fw.write(obj.nextLine()+"\n");
			}
			System.out.println("File Created Successfully");
			fw.close();
		}
		catch(Exception ex)
		{
			System.out.println("Some Error Occured");
	}
	}
	public static void deletefiles()
	{
		Scanner obj= new Scanner(System.in);
		try
		{
			String Filename;
			System.out.println("Enter File name you want to delete:");
			Filename= obj.nextLine();
			
			File fl=new File(projectpath+"\\"+Filename);
			
			if(fl.exists())
			{
				fl.delete();
				System.out.println("File Deleted Successfully");
			}
			else
			{
				System.out.println("File does not exist");
			}
		}
		catch(Exception ex)
		{
			System.out.println("Some Error Occured");
	}
		
	}
	public static void searchfiles()
	
	{
		Scanner obj=new Scanner(System.in);
		try
		{
			String Filename;
			System.out.println("Enter File name you want to Search:");
			Filename= obj.nextLine();
			
			File fl=new File(projectpath+"\\"+Filename);
			
			if(fl.exists())
			{
				System.out.println("File is Availabe");
			}
			else
			{
				System.out.println("File does not exist");
			}
		}
		catch(Exception ex)
		{
			System.out.println("Some Error Occured");
		}
	}
	
}

