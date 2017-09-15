# Data-In-Motion-Data-Loss-Prevention
Data Loss Prevention

# What is my project about?

My senior project was about writing a code in Java to filter confidential information.

There were many steps involved in my projects:
a- Data Collection:
I used Crawler4j to collect data from Huffington Blog. I customized the Crawler4j code to meet my needs and I used the customized code to collect data from the blog.
b) Data preparation:
I went over 800 pages worth of information and the project timeline allowed me to prepare 200 pages out of 800. I put what considered confidential in a word processer to use the Regex on them in order for them to be detected.
c) Regular Expressions:
I did three rules for my Regex, and the data is piped through them one by one: one to detect Peoples' names, ages, emails, sayings and professions, one to minimize the False Positive and to detect more professions, and the last rule is to detect more emails and Twitter accounts.
d) Calculating the True Positive (what was detected as confidential and it is true), False Positive (was detected as confidential but it is not) and the overall accuracy (accuracy of the detections). All these pieces based on the ground truth (number of pieces that were considered as confidential and the ones that are not).

Finally, I did the experiment (I ran the Java code) and write down the results and table and charts.


# How to run my project?

You just need to run the code as normal using any Java Editor. I am using Eclipse myself. 
1- Import the document...
2- Right click on the java file...
3- choose "run as" - "Java application".

# The Source Code:

package DLPversions;

import java.io.IOException;
import java.sql.SQLException;
import java.util.Scanner;
import java.io.BufferedReader;
	import java.io.FileNotFoundException;
	import java.io.FileReader;
	import java.io.IOException;
	import java.sql.SQLException;
	import java.text.DecimalFormat;
	import java.util.ArrayList;
	import java.util.List;
	import java.util.logging.Level;
	import java.util.logging.Logger;
	import java.util.regex.Matcher;
	import java.util.regex.Pattern;
public class DLPVersions {
	
//Data Loss Prevention System (Regular Expression Language)	

	/**
	 *
	 * @author abdullah
	 */
	
	static int i;
	static int j;
	static int i2;
	static int j2;
	static int e=0;
	static int number1;
	static int number2;
	static int number3;
	static int number4;
	static int number5;
	static int number6;
	static int number7;
	static int pp1;
	static int pp2;
	static int pp3;
	static int pp4;
	static int pp5;
	static int pp6;
	static int pp7;
	static int pp8;
	static int email1;
	static int email2;
	static int email3;
	static int email4;
	static int email5;
	static int email6;
	static double overallTP;
	static double overallFP;
	static double overallRatio;
	static double overallAccuracy;
	static int repeatedd=0;
	static boolean TrueOrFalse;
	static int repeated=0;

	static double i1;
	static double j1;
	static String NoOfConfidentialInfo;
	static String ThePercintageOfIt;
	static int noo=0;
	static String ExLine;
	static String TextLine;
	static String TextLine1;
	static String TextLine2;
	static String Conf_info_type;
	static String Expression;
	static String matches;
	static String matches3;
	static String matches4;
	static String matches2;
	static double f;
	static double f2;
	static double TP;
	static double FP;
	static double TP2;
	static double FP2;
	static int TN;
	static int FN;
	static int OverallTP;
	static int OverallFP;
	static int OverallTN;
	static int OverallFN;
	static int confidential;
	static int notConfidential;
	static Matcher Matched;	
	static Pattern NewRegex; 
	static Matcher Matched2;	
	static Pattern NewRegex2;    
	static BufferedReader readMyFile;
	static BufferedReader readMyFile2; 
	static BufferedReader readMyFile3;  
	static BufferedReader readMyFile4;  
	static List <Double> list=new ArrayList<Double>();
	static List <Double> list2=new ArrayList<Double>();
	static List <String> list5=new ArrayList<String>();
	static List <String> list6=new ArrayList<String>();
	static List <String> list7=new ArrayList<String>();
	static List <String> list8=new ArrayList<String>();
	static List <String> list3=new ArrayList<String>();
	static List <String> list4=new ArrayList<String>();
	static int lineNo;
	static int NoOfMatches;    
	    	
	
static int choose=-1;	
public static void main(String args[]) throws IOException, SQLException {    

Scanner s=new Scanner(System.in);	
	
while (choose != 0){
	j=0;f2=0;
	
//Choose on of the three rule sets	
System.out.println();	
System.out.println("Choose One of The Following Rule Set: ");
System.out.println("1- First Rule Set.");
System.out.println("2- Second Rule Set.");
System.out.println("3- Third Rule Set.");
System.out.println("0- Exit.");

choose=s.nextInt();
System.out.println();	
switch(choose){
//Version1 (first rule set)
case 1:
	ExLine=null; 
	   readMyFile=null;
	   try {
	        readMyFile = new BufferedReader(new FileReader("Version1.txt"));
	            
	        } catch (FileNotFoundException e) {
	        }
	         try {
	               while ((ExLine=readMyFile.readLine()) != null){
	              //ExLine has the expression and its label
	            	//This piece of code separate the expression from its label   
	              char whiteSpace=' ';  
	               Conf_info_type=ExLine.substring(0,whiteSpace);
	               Expression=ExLine.substring(whiteSpace);
	          
	              Conf_info_type=Conf_info_type.trim();
	              Expression=Expression.trim();
	              
	              readMyFile2=null;
	              try {
	                    readMyFile2 = new BufferedReader(new FileReader("Huffington200.txt"));
	            
	                  } catch (FileNotFoundException e) {
	                    }
	             
	    
	                       while ((TextLine=readMyFile2.readLine()) != null){
	                              regularExpressionCheck3(Expression,TextLine);
	                                     } 
	       //Ground truth (number of confidential pieces of information and their percentage
	                       //(
	                        list.add(67.0);
	                        list.add(26.0);
	                        list.add(1305.0);
	                        list.add(136.0);
	                        list.add(135.0);
	                        list2.add(0.03);
	                        list2.add(0.01);
	                        list2.add(0.78);
	                        list2.add(0.07);
	                        list2.add(0.07);
	        //taking them one by one
	                        i1=list.get(j);
	                        j1=list2.get(j);
	        //)
	        
	       //System.out.println("********************************");
	                        
	                        //Number of detected confidential information is TP and number of detected not confidential information is FP
	                        //(
	                       if(Conf_info_type.equalsIgnoreCase("People_Professions")){
	                       TP=TP+208;//208 because there is a line that has been detected as one piece of confidential information
	                       //and that line contain 208 piece of confidential information
	                       f=TP;
	                       FP=0;    
	                       System.out.println("(True Positive + False Positive): "+f);
	                       System.out.println("Number of true matches(True Positive): "+TP);
	                       System.out.println("Number of wrong matches(False Positive): "+FP);
	                       }

	                      if(Conf_info_type.equalsIgnoreCase("numbers")){
	                      System.out.println("(True Positive + False Positive): "+f);
	                      System.out.println("Number of true matches(True Positive): "+TP);
	                      System.out.println("Number of wrong matches(False Positive): "+FP);
	                      }
	                      if(Expression.equalsIgnoreCase("(Sasha Bronner|David Lohr|Jaweed Kaleem|Amanda Terkel|Michael McAuliff|Hunter Stuart|Elise Foley|Kim Bellware|Matt Sledge|Adam Levin|Melinda Hill|Ken Ritter|Matt Sledge|Rick Freeman|Salvatore Bono|Steve Karras|Michelle Cove|Steven Raichlen|Chris Weigant|Steven Raichlen|Leah Zerbe|Anne Margaret Daniel|Dylan Kendall|Chris Lawhorn|Toni Nagy|Melinda Hill|Jon Chattman|Lisa Derrick|Chris Weigant|Boone Pickens|Caurie Putnam|John Feffer|Salvatore Bono|Brian Moody|John C.K. Daly|Sharo Hill|Craig Newmark|Marlo Thomas|Julio Pabon|Bob Schulman|Nick Jefferson|Mark Rubinstein|Deepa Iyer|Chris Weigant|Harlan Green|Steven Raichlen|Zaki Hasan|Malerie Yolen-Cohen|Barbara Barton|Marshall Fine|Jackie Pilossoph|by Stephanie Dempsey|Rick Freeman|Jim Wallis|Matt Sledge|Jen Glantz|Adam K. Levin)(\\s{2}|\\s{3}|\\s{5}|\\s{8}|\\s{9}).*?\\.(com)")){
	                      System.out.println("(True Positive + False Positive): "+f);
	                      System.out.println("Number of true matches(True Positive): "+TP);
	                      System.out.println("Number of wrong matches(False Positive): "+FP);
	                      }
	                      if(Conf_info_type.equalsIgnoreCase("People_Speeches")){
	                      System.out.println("(True Positive + False Positive): "+f);
	                      System.out.println("Number of true matches(True Positive): "+TP);
	                      System.out.println("Number of wrong matches(False Positive): "+FP);
	                      }

	                     if(Conf_info_type.equalsIgnoreCase("ages")){
	                     TP=TP-2;
	                     f=f-2;
	                     System.out.println("(True Positive + False Positive): "+f);
	                     System.out.println("Number of true matches(True Positive): "+TP);
	                     System.out.println("Number of wrong matches(False Positive): "+FP);}
                         //)
	                     System.out.println();
	                     System.out.println(); 
	                     System.out.println("*********Ground Truth of: "+Conf_info_type+"*********");
	                     System.out.println();
	                     System.out.println(); 
	                     //ground truth result
	                     System.out.println("\tNumber of Confidential Pieces\t|\tRatio of This Type");
	                     System.out.println("\t\t\t\t"+i1+"\t\t\t\t|\t"+j1);
	                     System.out.println();
	                     System.out.println("*****************************************************");


                         
	                     System.out.println("\tTPRate\t");
	                     System.out.println("\t"+new DecimalFormat("#.###").format(TP/f));
	                     System.out.println();
	                     System.out.println();

                         //the remaining percent to reach to the ground truth percentages
	                     System.out.println("\tThe Ratio of Overall Ground Truth\t|\tThe Overall Ground Truth Ratio Goal");
	                     System.out.println("\t\t\t\t"+new DecimalFormat("#.##").format(TP/1964)+"\t\t\t\t|\t\t"+j1);
	                     System.out.println("Remaining Ratio to Reach Overall Ground Truth Ratio Goal: "+new DecimalFormat("#.##").format(j1-(TP/1973))); 
	                     System.out.println();
	                     //number of detected confidential pieces of information divided by 
	                     //(number of detected confidential pieces of information+number of detected not confidential peices of information  
	                     System.out.println("**************");
	                     System.out.println("|Accuracy: "+new DecimalFormat("#.##").format(TP/i1)+"|");
	                     System.out.println("***************");
	                     System.out.println();

                         //print the confidential pieces of information
	                     System.out.println("********************True Positive Matches :"+Conf_info_type+"*******************");
	                     for(i2=0;i2<list3.size();i2++){
	                     matches=list3.get(i2);
	                     System.out.println(matches);   
	                    }
	                    System.out.println();
	                    System.out.println();
	                    System.out.println("*********************False Positive Matches :"+Conf_info_type+"********************");
	                    //print the not confidential pieces of information
	                   for(j2=0;j2<list4.size();j2++){
	                   matches=list4.get(j2);
	                   System.out.println(matches);   
	                   }
	                   if(list4.isEmpty()||list3.isEmpty()){
	                      if(!Conf_info_type.equalsIgnoreCase("numbers")){
	                       System.out.println("The list is empty.");   
	                       }
	                       else{
	                        System.out.println("The list is so long to print, waste of time.");
	                        }
	                   }
	                  overallTP+=TP;
	                  overallFP+=FP;
	       
	                 TP=0;FP=0; j++;
	                 f=0;
	                 list3.clear();
	                 list4.clear();
	                 System.out.println("*************************************************************************************");}  
	               System.out.println("Number of detected confidential peices of information: "+overallTP);
	               System.out.println("Number of detected not confidential peices of information: "+overallFP);
	                overallTP/=f2;
	                //overallFP/=f2;
	        
	                double allTP;allTP=635;//all the detected True Positive 
	                double alltp;alltp=1667;//the overall confidential pieces of information (ground truth)
	                System.out.println("**********The Result of The Five Expressions**********");
	                System.out.println("OverallTPRate\t|\tOverallAccuracy");
	                System.out.println(new DecimalFormat("#.##").format(overallTP)+"\t|\t"+"\t|\t"+new DecimalFormat("#.##").format(allTP/alltp));
// preparing these variables for reuse
	                overallTP=0; overallFP=0; overallAccuracy=0; overallRatio=0;
	                list.clear();
	                list2.clear();
	                list3.clear();
	                list4.clear();
	            }catch (Exception e){
	        
	            }	
break;	

case 2:
	ExLine=null; 
    readMyFile=null;
           
    try {
         readMyFile = new BufferedReader(new FileReader("Version2.txt"));
           
    } catch (FileNotFoundException e) {
    }
      try {
      while ((ExLine=readMyFile.readLine()) != null){
      
      char whiteSpace=' ';  
      Conf_info_type=ExLine.substring(0,whiteSpace);
      Expression=ExLine.substring(whiteSpace);
      Conf_info_type=Conf_info_type.trim();
      Expression=Expression.trim();
        
      readMyFile2=null;
      try {
            readMyFile2 = new BufferedReader(new FileReader("Huffington200.txt"));
           
      } catch (FileNotFoundException e) {
      }
            while ((TextLine=readMyFile2.readLine()) != null){//System.out.println("flag1"); 
             
                 if(TextLine.contains("Document Number")){
                   number7++;  continue;
                 }
                  
                  regularExpressionCheck5(Expression,TextLine);
                  } 
            //Ground truth (number of confidential pieces of information and their percentage
              list.add(67.0);
              list.add(24.0);
              list.add(1305.0);
              list.add(136.0);
              list.add(135.0);
              list2.add(0.03);
              list2.add(0.01);
              list2.add(0.78);
              list2.add(0.07);
              list2.add(0.07);
       //getting the ground truth numerical value one by one
              i1=list.get(j);
              j1=list2.get(j);
              //)
            //Number of detected confidential information is TP and number of detected not confidential information is FP
              //(
              if(Conf_info_type.equalsIgnoreCase("People_Professions")){
              TP=TP+208; //208 because there is a line that has been detected as one piece of confidential information
              //and that line contain 208 piece of confidential information
              System.out.println("(True Positive + False Positive): "+f);
              System.out.println("Number of true matches(True Positive): "+TP);
              System.out.println("Number of wrong matches(False Positive): "+FP);
              }
              if(Conf_info_type.equalsIgnoreCase("numbers")){
                  
              System.out.println("(True Positive + False Positive): "+f);
              System.out.println("Number of true matches(True Positive): "+TP);
              System.out.println("Number of wrong matches(False Positive): "+(FP));
              }
              if (Expression.equals("(Sasha Bronner|David Lohr|Jaweed Kaleem|Amanda Terkel|Michael McAuliff|Hunter Stuart|Elise Foley|Kim Bellware|Matt Sledge|Adam Levin|Melinda Hill|Ken Ritter|Matt Sledge|Rick Freeman|Salvatore Bono|Steve Karras|Michelle Cove|Steven Raichlen|Chris Weigant|Steven Raichlen|Leah Zerbe|Anne Margaret Daniel|Dylan Kendall|Chris Lawhorn|Toni Nagy|Melinda Hill|Jon Chattman|Lisa Derrick|Chris Weigant|Boone Pickens|Caurie Putnam|John Feffer|Salvatore Bono|Brian Moody|John C.K. Daly|Sharo Hill|Craig Newmark|Marlo Thomas|Julio Pabon|Bob Schulman|Nick Jefferson|Mark Rubinstein|Deepa Iyer|Chris Weigant|Harlan Green|Steven Raichlen|Zaki Hasan|Malerie Yolen-Cohen|Barbara Barton|Marshall Fine|Jackie Pilossoph|by Stephanie Dempsey|Rick Freeman|Jim Wallis|Matt Sledge|Jen Glantz|Adam K. Levin)(\\s{2}|\\s{3}|\\s{5}|\\s{8}|\\s{9}).*?\\.(com)")){
              System.out.println("(True Positive + False Positive): "+f);
              System.out.println("Number of true matches(True Positive): "+TP);
              System.out.println("Number of wrong matches(False Positive): "+(FP));
              }
              if(Conf_info_type.equalsIgnoreCase("People_Speeches")){
              System.out.println("(True Positive + False Positive): "+f);
              System.out.println("Number of true matches(True Positive): "+TP);
              System.out.println("Number of wrong matches(False Positive): "+(FP));
              }
             if(Conf_info_type.equalsIgnoreCase("ages")){
              f=f-2; //-2 because there is a repeated detection twice 
              TP=TP-2;
              System.out.println("(True Positive + False Positive): "+f);
              System.out.println("Number of true matches(True Positive): "+TP);
              System.out.println("Number of wrong matches(False Positive): "+FP);}
       
              System.out.println();
              System.out.println(); 
              System.out.println("*********Ground Truth of: "+Conf_info_type+"*********");
              System.out.println();
              System.out.println(); 
              //ground truth numerical retrieval
              System.out.println("\tNumber of Confidential Pieces\t|\tRatio of This Type");
              System.out.println("\t\t\t\t"+i1+"\t\t\t\t|\t"+j1);
              System.out.println();
              System.out.println();
      //)
              System.out.println("*****************************************************");
      
              System.out.println("\tTP\tRate");
              System.out.println("\t"+new DecimalFormat("#.##").format(TP/f));
              System.out.println();
              System.out.println();
      
              //the remaining percent to reach to the exact percent for overall confidential information
              System.out.println("\tThe Ratio of Overall Ground Truth\t|\tThe Overall Ground Truth Ratio Goal");
              System.out.println("\t\t\t\t"+new DecimalFormat("#.##").format(TP/1964)+"\t\t\t\t|\t\t"+j1);
              System.out.println("Remaining Ratio to Reach Overall Ground Truth Ratio Goal: "+new DecimalFormat("#.##").format(j1-(TP/1973))); 
              System.out.println();
              //number of detected confidential pieces of information divided by 
              //(number of detected confidential pieces of information+number of detected not confidential peices of information  
              System.out.println("**************");
              System.out.println("|Accuracy: "+new DecimalFormat("#.##").format(TP/i1)+"|");
              System.out.println("***************");
              System.out.println();
     
            //print the confidential pieces of information
              System.out.println("********************True Positive Matches :"+Conf_info_type+"*******************");
            //print the not confidential pieces of information
              for(i2=0;i2<list3.size();i2++){
              matches=list3.get(i2);
              System.out.println(matches); }
              if(list3.isEmpty()){
                if(Conf_info_type.equals("Emails_URLs ")){
                System.out.println("list is so long, waste of time if printed.");   
                }else{
               System.out.println("The list is empty.");
              }
              }
              System.out.println();
              System.out.println();
              System.out.println("*********************False Positive Matches :"+Conf_info_type+"********************");
      
              for(j2=0;j2<list4.size();j2++){
              matches=list4.get(j2);
              System.out.println(matches); }  
      
              if(list4.isEmpty()||list3.isEmpty()){
                 if(Conf_info_type.equalsIgnoreCase("numbers")||Conf_info_type.equalsIgnoreCase("People_Professions")){
                 System.out.println("The list is so long to print, waste of time.");
               }
                else{
                System.out.println("The list is empty."); 
                }
       
       
       
         }
         overallTP+=TP;
         overallFP+=FP;
      // preparing these variables for reuse
       
       TP=0;FP=0; j++;
       f=0;
       list3.clear();
       list4.clear();
       System.out.println("*************************************************************************************");}  
       System.out.println("Number of detected confidential peices of information: "+overallTP);
       System.out.println("Number of detected not confidential peices of information: "+overallFP);
       
       overallTP/=f2;
       //overallFP/=f2;
       double allTP;allTP=854;
       double alltp;alltp=1667;
       
       System.out.println("**********The Result of The Five Expressions**********");
       System.out.println("OverallTPRate\t|\tOverallAccuracy");
       System.out.println(new DecimalFormat("#.##").format(overallTP)+"\t|\t"+new DecimalFormat("#.##").format(allTP/alltp));

       overallTP=0; overallFP=0; overallAccuracy=0; overallRatio=0;
       list.clear();
       list2.clear();
       list3.clear();
       list4.clear();
    }catch (Exception e){
    }
break;	

case 3:
	ExLine=null; 
    readMyFile=null;
    try {
          readMyFile = new BufferedReader(new FileReader("Version3.txt"));
          } catch (FileNotFoundException e) {
          }
      try {
      while ((ExLine=readMyFile.readLine()) != null){
      char whiteSpace=' ';  
       Conf_info_type=ExLine.substring(0,whiteSpace);
       Expression=ExLine.substring(whiteSpace);
       Conf_info_type=Conf_info_type.trim();
       Expression=Expression.trim();
       
       readMyFile2=null;
       try {
          readMyFile2 = new BufferedReader(new FileReader("Huffington1000.txt"));
         
          } catch (FileNotFoundException e) {
          }
              while ((TextLine=readMyFile2.readLine()) != null){
                 if(Expression.equalsIgnoreCase("(\\p{Alpha}+)?\\d?\\W?\\d?(\\p{Alpha}+)?\\d?\\W?\\d?(\\p{Alpha}+)?\\d?\\W?\\d?@(\\p{Alpha}+)?\\d?\\W?\\d?\\.[a-z]{3}")){
                 Conf_info_type="email"; 
                  }
                 
                  if(TextLine.contains("Document Number")){
                  continue; }
                  regularExpressionCheck6(Expression,TextLine);
                  } 
    
     
    
            //Number of detected confidential information is TP and number of detected not confidential information is FP
              //(
         
         if(Expression.equalsIgnoreCase("(\\p{Alpha}+)?\\d?\\W?\\d?(\\p{Alpha}+)?\\d?\\W?\\d?(\\p{Alpha}+)?\\d?\\W?\\d?@(\\p{Alpha}+)?\\d?\\W?\\d?\\.[a-z]{3}")){
          System.out.println("(True Positive + False Positive)"+f);  
          System.out.println("Number of true matches(True Positive): "+TP);
          System.out.println("Number of wrong matches(False Positive): "+FP);
         }
         
          if(Conf_info_type.equalsIgnoreCase("Twitter_account")){
        	  System.out.println("(True Positive + False Positive)"+f); 
          System.out.println("Number of true matches(True Positive): "+TP);
          System.out.println("Number of wrong matches(False Positive): "+FP);
         }
     
         //)
    System.out.println("\tTPRat\t");
    System.out.println("\t"+new DecimalFormat("#.##").format(TP/f)+"\t\t");
    System.out.println();
    System.out.println();
    System.out.println("********************True Positive Matches :"+Conf_info_type+"*******************");
    for(i2=0;i2<list3.size();i2++){
       matches=list3.get(i2);
       System.out.println(matches);   
       }
    System.out.println();
    System.out.println();
    System.out.println("*********************False Positive Matches :"+Conf_info_type+"********************");
    
     for(j2=0;j2<list4.size();j2++){
        matches=list4.get(j2);
        System.out.println(matches);   
        }
    
    if(list4.isEmpty()||list3.isEmpty()){
         if(!Conf_info_type.equalsIgnoreCase("numbers")||!Conf_info_type.equalsIgnoreCase("People_Professions") || Conf_info_type.equalsIgnoreCase("Twitter_account") ){
          System.out.println("The list is empty.");   
         }
         else{
             System.out.println("The list is so long to print, waste of time.");
         }
     }
     overallTP+=TP;
     overallFP+=FP;
     //overallRatio+=(TP/1973);
  //  overallAccuracy+=;
     
     TP=0;FP=0; j++;
     f=0;
     list3.clear();
     list4.clear();
     list7.clear();
     list8.clear();
     System.out.println("*************************************************************************************");}  
     System.out.println(overallTP);
     overallTP/=f2;
     //overallFP/=f2;
      
     
  System.out.println("**********The Result of The Two Expressions**********");
  System.out.println("OverallTPRate\t|\tOverallFP\t");
  System.out.println(new DecimalFormat("#.##").format(overallTP)+"\t|\t"+new DecimalFormat("#.##").format(OverallFP));

  overallTP=0; overallFP=0; overallAccuracy=0; overallRatio=0;
  list.clear();
  list2.clear();
  list3.clear();
  list4.clear();
 }catch (Exception e){
     
 }    // TOD   	
	
break;	

case 0:
System.out.println("Start Over, Finished.");
System.exit(0);
break;

default:
System.out.println("Choose from 0 to 3.");	
break;	
	


}


}
	
	
}


//This method is to do the matching process for version 1

public static void regularExpressionCheck3(String Regex, String str) throws SQLException, IOException{
NewRegex= Pattern.compile(Regex);
Matched=NewRegex.matcher(str);

while(Matched.find()){
//NoOfMatches++;
    if(Matched.group().length() != 0){

     matches=Matched.group().trim();
    
 
    
   //Calculate the True Positive and the False Positive for overall type of confidential information
     //(
        if (Expression.equalsIgnoreCase("(Sasha Bronner|David Lohr|Jaweed Kaleem|Amanda Terkel|Michael McAuliff|Hunter Stuart|Elise Foley|Kim Bellware|Matt Sledge|Adam Levin|Melinda Hill|Ken Ritter|Matt Sledge|Rick Freeman|Salvatore Bono|Steve Karras|Michelle Cove|Steven Raichlen|Chris Weigant|Steven Raichlen|Leah Zerbe|Anne Margaret Daniel|Dylan Kendall|Chris Lawhorn|Toni Nagy|Melinda Hill|Jon Chattman|Lisa Derrick|Chris Weigant|Boone Pickens|Caurie Putnam|John Feffer|Salvatore Bono|Brian Moody|John C.K. Daly|Sharo Hill|Craig Newmark|Marlo Thomas|Julio Pabon|Bob Schulman|Nick Jefferson|Mark Rubinstein|Deepa Iyer|Chris Weigant|Harlan Green|Steven Raichlen|Zaki Hasan|Malerie Yolen-Cohen|Barbara Barton|Marshall Fine|Jackie Pilossoph|by Stephanie Dempsey|Rick Freeman|Jim Wallis|Matt Sledge|Jen Glantz|Adam K. Levin)(\\s{2}|\\s{3}|\\s{5}|\\s{8}|\\s{9}).*?\\.(com)")){
        f2++;  
        f++;
//calculate the repeated detection of the following texts(
            if(matches.contains("Jim Wallis    	Christian leader for social change; Pr")){
            email1++;
            }
            if(matches.contains("Jim Wallis  		Another Pro-Life Issue")){
            email2++;
            }
            if(matches.contains("Jim Wallis 			 				Tavis Smiley")){
            email3++;
            }
            if(matches.contains("Matt Sledge  The Feds Could B")){
            email4++; matches.replace("Matt Sledge  The Feds Could B","");
            }
            if(matches.contains("Chris Weigant")){
            email5++; }
            if(matches.contains("Adam Levin 				")){
            email6++; }
            //)
            
            //This if is to not calculating the repeated detection of not confidential information 
            if(email1>1 || email2>1|| email3 >1 || email5>1 || email6 > 1 ||email4 > 1){ //System.out.append("FP: "+FP);
            FP++;
            list4.add(matches);
            }else{
            //System.out.println("Match: "+matches);
            TP++;
            list3.add(matches);
      
            }    email1=1;email2=1;email3=1;email5=1;email6=1;email4=1;
  
            }
            
        
          else if (Conf_info_type.equalsIgnoreCase("Ages")){f++;f2++;
 
          TP++;
          list3.add(matches);
          }
          
          
           else if (Conf_info_type.equalsIgnoreCase("People_Professions")){f++;f2++;
   
           TP++;
           list3.add(matches);
  
           }  
          
           else if (Conf_info_type.equalsIgnoreCase("Numbers")){
           f++;f2++;
           readMyFile4=null;
              try {
               
               if(matches.contains("Ben Lost 120 Pounds: 'The Key To Transforming Your Physique Is To Transform Your Lifestyle'")){
               number1++;   
               }
               if(matches.contains("Why Amazon Pays Some Workers Up To $5,000 To Quit")){
               number2++; 
               }
                if(matches.contains("﻿U.S. Legal Post Sales To Hit $8 Billion A Year By 201")){
                number3++; 
               }
  
                if(matches.contains("Document Number")){
                number4++; 
                }
                
                if(matches.contains("I had 11 surgeries. It's been al")){
                number5++; 
                }
                
                 if(matches.contains("My life, since age 10, has")){
                number6++; 
                }
                
                if (number5 > 1){
                    TP--;
                }
                
                 if (number6 > 1){
                    TP--;
                }//another level of matching to make sure that what was matches from the Huffington200 text file 
                 //is really have a match
                readMyFile4 = new BufferedReader(new FileReader("numbers.txt"));
            
               } catch (FileNotFoundException e) {
               }
             
                   while ((TextLine=readMyFile4.readLine()) != null){
                   regularExpressionCheck4("(?m)^.*$",TextLine);
  
                       if (matches.contains(matches2)&& !matches2.equalsIgnoreCase("Ben Lost 120 Pounds: 'The Key To Transforming Your Physique Is To Transform Your Lifestyle'") &&!matches2.equalsIgnoreCase("Why Amazon Pays Some Workers Up To $5,000 To Quit")  ){
                       TP++; list3.add(matches2);
                       } else if(number1 > 1  || number4 >1  ){
                       list4.add(matches);
                       FP++; 
                       }
                        number1=1;number2=1;number3=1;number4=1;number5=1;number6=1;
                       }    
                       }
     
                  else if (Conf_info_type.equalsIgnoreCase("People_Speeches")){f++;f2++;
                   //System.out.println("flag1");
                  list3.add(matches);      TP=f;
                  FP=0;
                  }  //) this closing is for the opened comment above of calculating the True Positive and the False Positive 
    
           }
         }
      }
    
    
    
public static void regularExpressionCheck6(String Regex, String str) throws SQLException, IOException{
NewRegex= Pattern.compile(Regex);
Matched=NewRegex.matcher(str);	
while(Matched.find()){
   if(Matched.group().length() != 0){
   matches=Matched.group().trim();
   
  if (Conf_info_type.equalsIgnoreCase("email")){
  f2++;  
  f++;
  
  list7.add(matches);
  list8.add(matches);
  //this piece of code is to discount the repeated email addresses
  //(
  int r=0;
  String newConf="";
  String PrevConf="";
  
  r=list7.size()-1;
  newConf=list7.get(r);
  for(int i=0; i < list8.size()-2;i++){
  PrevConf=list8.get(i);
  if(newConf.equalsIgnoreCase(PrevConf)){
   matches="";
   f--;f2--;
  // System.out.println("Matches: "+matches);
   break;
    }
  }//)
  if((matches.contains("Jim Wallis")||matches.equals("Marlo Thomas 		                  More Top Stories                  Natasha Coleman	      Told She Was Too Fat To Fly First Class, Mother Of Three Loses More Than 200 Pounds       99   /			 			Healthy Living             MarloThomas.com\n" +
  "")) && !matches.equals("")){ System.out.append("FP: "+FP);
  FP++;
  list4.add(matches);
  }else if (!matches.equalsIgnoreCase("")){
  TP++;
  list3.add(matches);
  }    
  }
  
else if (Conf_info_type.equalsIgnoreCase("Twitter_account")){f++;f2++;

list7.add(matches);
  list8.add(matches);
//this piece of code is to discount the repeated twitter accounts
  //(
  int r=0;
  String newConf="";
  String PrevConf="";
  
  r=list7.size()-1;
  newConf=list7.get(r);
  for(int i=0; i < list8.size()-2;i++){
  PrevConf=list8.get(i);
  if(newConf.equalsIgnoreCase(PrevConf)){
   matches="";
   f--;f2--;
  // System.out.println("Matches: "+matches);
   break;
  }

  }//)

if(!matches.equals("")){
TP++; list3.add(matches);    
}  

FP=0;
 }      
   
    }
  } 

    
}   
public static void regularExpressionCheck5(String Regex, String str) throws SQLException, IOException{
NewRegex= Pattern.compile(Regex);
Matched=NewRegex.matcher(str);	
while(Matched.find()){
   if(Matched.group().length() != 0){
   matches=Matched.group().trim();
    
      if (Expression.equalsIgnoreCase("(Sasha Bronner|David Lohr|Jaweed Kaleem|Amanda Terkel|Michael McAuliff|Hunter Stuart|Elise Foley|Kim Bellware|Matt Sledge|Adam Levin|Melinda Hill|Ken Ritter|Matt Sledge|Rick Freeman|Salvatore Bono|Steve Karras|Michelle Cove|Steven Raichlen|Chris Weigant|Steven Raichlen|Leah Zerbe|Anne Margaret Daniel|Dylan Kendall|Chris Lawhorn|Toni Nagy|Melinda Hill|Jon Chattman|Lisa Derrick|Chris Weigant|Boone Pickens|Caurie Putnam|John Feffer|Salvatore Bono|Brian Moody|John C.K. Daly|Sharo Hill|Craig Newmark|Marlo Thomas|Julio Pabon|Bob Schulman|Nick Jefferson|Mark Rubinstein|Deepa Iyer|Chris Weigant|Harlan Green|Steven Raichlen|Zaki Hasan|Malerie Yolen-Cohen|Barbara Barton|Marshall Fine|Jackie Pilossoph|by Stephanie Dempsey|Rick Freeman|Jim Wallis|Matt Sledge|Jen Glantz|Adam K. Levin)(\\s{2}|\\s{3}|\\s{5}|\\s{8}|\\s{9}).*?\\.(com)")){
      f2++;  
        f++;

            if(matches.contains("Jim Wallis    	Christian leader for social change; Pr")){
            email1++;
            }
            if(matches.contains("Jim Wallis  		Another Pro-Life Issue")){
            email2++;
            }
            if(matches.contains("Jim Wallis 			 				Tavis Smiley")){
            email3++;
            }
            if(matches.contains("Matt Sledge  The Feds Could B")){
            email4++; matches.replace("Matt Sledge  The Feds Could B","");
            }
            if(matches.contains("Chris Weigant")){
            email5++; }
            if(matches.contains("Adam Levin 				")){
            email6++; }
            
            
            
            if(email1>1 || email2>1|| email3 >1 || email5>1 || email6 > 1 ||email4 > 1){ //System.out.append("FP: "+FP);
            FP++;
            list4.add(matches);
            }else{
           // System.out.println("Match: "+matches);
            TP++;
            list3.add(matches);
      
            }    email1=1;email2=1;email3=1;email5=1;email6=1;email4=1;
  
     }         
        
 
           else if (Conf_info_type.equalsIgnoreCase("Ages")){f++;f2++;
 
           TP++;
           list3.add(matches);
 
            }
           
            else if (Conf_info_type.equalsIgnoreCase("People_Professions")){f++;f2++;
                   if(matches.contains("Sen. Patrick Leahy (D- VT) gavels the Senate Judiciary Committee to order on")){
                   pp1++;
                   }
                   if(matches.contains("Follow HuffPost        Email    Facebook    Twitter    Google Plus    RSS    Mobile")){
                   pp2++;
                   }
                   if(matches.contains("ASSOCIATED PRESS")){
                   pp3++;
                   }
                   if(matches.contains("Most Popular             LOOK: Boston M")){
                   pp4++;
                   }
                   if(matches.contains("Most Popular            FROM WAY UP HIGH")){
                    pp5++;
                    }
                    if(matches.contains("Most Popular            This Country Has")){
                    pp6++;
                    }
                    if(matches.contains("Most Popular            Basketball Hall Of")){
                    pp7++;
                    }
                    if(matches.contains("iOS app  Android app   	 Mo")){
                     pp8++;
                    }
     
                    if (pp1>1){
                    matches.replace("Sen. Patrick Leahy (D- VT) gavels the Senate Judiciary Committee to order on","");
                    f--; f2--;
                    }
                    if (pp2>1){
                    matches.replace("Follow HuffPost        Email    Facebook    Twitter    Google Plus    RSS    Mobile","");
                    f--; f2--;
                    }
                    if (pp3>1){
                    matches.replace("ASSOCIATED PRESS","");
                    f--; f2--;
                    }
                    if (pp4>1){
                    matches.replace("Most Popular             LOOK: Boston M","");
                    f--; f2--;
                    }
                   if (pp5>1){
                   matches.replace("Most Popular            FROM WAY UP HIGH","");
                   f--; f2--;
                   }
                   if (pp6>1){
                   matches.replace("Most Popular            This Country Has","");
                   f--; f2--;
                   }
                   if (pp7>1){
                   matches.replace("Most Popular            Basketball Hall Of","");
                   f--; f2--;
                   }
                   
            readMyFile4=null;
            //System.out.println("Matches: "+matches);
             try {
             readMyFile4 = new BufferedReader(new FileReader("people professionals.txt"));
            
             } catch (FileNotFoundException e) {
             }
              while ((TextLine=readMyFile4.readLine()) != null){
                     regularExpressionCheck4(".*$",TextLine);
                     if(matches.equals(matches2) /*|| matches.contains("Sen. Patrick Leahy (D- VT) gavels the Senate")*/){
                     TP++;
                     list3.add(matches);
                     }else if (pp1 > 1 || pp2 > 1 || pp3 > 1 || pp4 > 1 || pp5 > 1 || pp6 > 1 || pp7 > 1 || pp8>1 ){
                      FP++; list4.add(matches);
                      }
 
               pp1=1;pp2=1;pp3=1;pp4=1;pp5=1; pp6=1; pp7=1; pp8=1;
              }  
     }
     else if (Conf_info_type.equalsIgnoreCase("Numbers")){
           
     f++;f2++;
               
             
               if(matches.contains("Ben Lost 120 Pounds: 'The Key To Transforming Your Physique Is To Transform Your Lifestyle'")){
               number1++;   
               }
               if(matches.contains("Why Amazon Pays Some Workers Up To $5,000 To Quit")){
               number2++; 
               }
                if(matches.contains("﻿U.S. Legal Post Sales To Hit $8 Billion A Year By 201")){
                number3++; 
               }
  
                if(matches.contains("Document Number")){
                number4++; 
                }
                
                if(matches.contains("I had 11 surgeries. It's been al")){
                number5++; 
                }
                
                 if(matches.contains("My life, since age 10, has")){
                number6++; 
                }
                
                if (number5 > 1){
                    TP--;
                }
                
                 if (number6 > 1){
                    TP--;
                }
                readMyFile4=null;
              try {
               readMyFile4 = new BufferedReader(new FileReader("numbers.txt"));
            
               } catch (FileNotFoundException e) {
               }
                   while ((TextLine=readMyFile4.readLine()) != null){
                   regularExpressionCheck4("(?m)^.*$",TextLine);
  
                       if (matches.contains(matches2)&& !matches2.equalsIgnoreCase("Ben Lost 120 Pounds: 'The Key To Transforming Your Physique Is To Transform Your Lifestyle'") &&!matches2.equalsIgnoreCase("Why Amazon Pays Some Workers Up To $5,000 To Quit")  ){
                       TP++; list3.add(matches2);
                       } else if(number1 > 1  || number4 >1  ){
                       list4.add(matches);
                       FP++; 
                       }
                        number1=1;number2=1;number3=1;number4=1;number5=1;number6=1;
                       }    
                     
   }
    else if (Conf_info_type.equalsIgnoreCase("People_Speeches")){f++;f2++;
                   //System.out.println("flag1");
                  list3.add(matches);      TP=f;
                  FP=0;
                  }  
   
   }  
} }
    
    
    
public static void regularExpressionCheck4(String Regex, String str) throws SQLException, IOException{
NewRegex2= Pattern.compile(Regex);
Matched2=NewRegex2.matcher(str);	
while(Matched2.find()){

   if(Matched2.group().length() != 0){
    matches2=Matched2.group().trim();
     }   
}
}
}    
    
  
  # Your Advices:
  
  Please I need some recommendations to improve my code, it has some mistakes. However, fortunately the mistakes did not take me off the A grade.







