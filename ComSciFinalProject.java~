/* Com Sci Final Project
 * Desc: ComSci final project game
 * @author Angelina Zhang
 * @version Dec 2017
 */

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.io.File;
import java.io.*;
import java.io.IOException;
import javax.imageio.ImageIO;
import java.awt.image.BufferedImage;
import java.util.Scanner;

public class ComSciFinalProject{ 
    static JFrame gameWindow;
    static GraphicsPanel canvas;
    
    //gameWindow Settings
    static final int WIDTH = 800;
    static final int HEIGHT = 600;
    static final int TOP = 0;
    static final int BOTTOM = 565;
    static final int LEFT = 0;
    static final int RIGHT = 780;
    
    // key listener and mouse Listener 
    static MyKeyListener keyListener = new MyKeyListener(); 
    static MyMouseListener mouseListener = new MyMouseListener(); 
    static MyMouseMotionListener mouseMotionListener = new MyMouseMotionListener(); 
    
    // background properties
    static int backgroundX = 0;
    static int backgroundY = 0;
    static int backgroundH;
    static int backgroundW;
    //speed for background movement
    static int stepX = 20; 
    
    // character properties
    static final int GROUND_LEVEL = 500;
    static final int mcH = 150;
    static final int mcW = 90; 
    static int mcX = 322 ; 
    static final int mcY = GROUND_LEVEL-mcH;
    static int mcVx = 20; 
    static int mcPicNum = 1; 
    static String mcState = "standing left";
    static BufferedImage[] mcPic = new BufferedImage[9];
    static int[] nextLeftPic =  {1, 2, 3, 1, 1, 1, 1, 1, 1, 1, 1, 1};
    static int[] nextRightPic = {4, 4, 4, 4, 5, 6, 7, 5, 4, 4, 4, 4};
    
    //title display
    static BufferedImage title;
    static int randTitle;  
    
    //Button properties 
    static BufferedImage startButton; 
    static BufferedImage instruButton; 
    static BufferedImage backButton;
    static final int buttonW = 153;
    static final int buttonH = 60; 
    static final int allButtonX = 320;
    static final int startY = 331;
    static final int instruY = 414;
    
    //character pictures 
    static BufferedImage character1; 
    static BufferedImage character2; 
    static BufferedImage nurse;
    static BufferedImage textBox; 
    
    //background images 
    static BufferedImage background;
    static BufferedImage brush;
    static BufferedImage brushZoomUp;
    static BufferedImage safeZoomUp;
    static BufferedImage intro; 
    static BufferedImage instructionsPage;
    
    //Office room items 
    static BufferedImage office; 
    static BufferedImage docNote;
    static BufferedImage nurseSticky; 
    static BufferedImage bottleNote; 
    static BufferedImage calendar; 
    static BufferedImage phoneLocked; 
    static BufferedImage phoneUnlocked; 
    static BufferedImage keypad;
    
    //office room item properties 
    static int docNoteX =216; 
    static int docNoteY = 347;
    static int docNoteW = 250-216;
    static int docNoteH = 385 - 347;
    static int nurseStickyX=641;
    static int nurseStickyY = 443;
    static int nurseStickyW = 678 - 641;
    static int nurseStickyH = 462- 443;
    static int bottleNoteX =532;
    static int bottleNoteY = 375;
    static int bottleNoteW = 583-532;
    static int bottleNoteH = 394- 375;
    static int phoneDrawerX =276;
    static int phoneDrawerY = 400;
    static int phoneDrawerW = 395-276;
    static int phoneDrawerH = 419- 400;
    static int calendarX = 697;
    static int calendarY = 265;
    static int calendarW = 782-697;
    static int calendarH = 360-265;
    
    //back button on the instructions page and office room
    static final int backX = RIGHT - buttonW;
    static final int backY = BOTTOM - buttonH; 
    
    //buttons for chosing passcodes 
    static BufferedImage phonePasscode;
    static BufferedImage character1Passcode;
    static BufferedImage character2Passcode; 
    
    //background when talking to characters
    static BufferedImage c1TalkBackground;
    static BufferedImage c2TalkBackground;
    static BufferedImage mcRoom; 
    
    //endings 
    static BufferedImage c1EndingImage;
    static BufferedImage c2EndingImage;
    static String HasSeenEnding = "HasSeenEnding.txt";
    static BufferedImage trueEndingBackground; 
    
    //Boolean Value for switching pages 
    static Boolean titleDisplay = true; 
    static Boolean gamePlay = false;
    static Boolean instructions = false; 
    static Boolean introAnimation = false; 
    static Boolean officeRoom = false; 
    static Boolean exit = false;
    static Boolean drawMcRoom = false;
    static Boolean drawBrush = false;
    static Boolean drawSafe = false;
    
    //drawing each item in the office
    static Boolean drawDocNote = false;
    static Boolean drawNurseSticky = false;
    static Boolean drawBottleNote = false;
    static Boolean drawPhone= false;
    static Boolean drawCalendar = false; 
    
    //flag to triggered the stages of dialogue 
    static Boolean phase2Flag = false;
    static Boolean phase3Flag = false;
    
    //flag that trigger the numbers being found
    static Boolean num1IsKnown = false;
    static Boolean num2IsKnown = false; 
    static Boolean num3IsKnown = false;
    static Boolean num4IsKnown = false; 
    
    //exit option 
    static Boolean exitOption = false;
    static Boolean drawExitOption = false;
    static Boolean endGame = false;
    
    //coordinate for rectangles 
    static int door1X = 40+322;
    static int door2X = 600+322;
    static int mcDoorX = 644;
    static int officeDoorX = 323+800+322;
    static int exitDoorX = 1600+288+322;
    static int safeX = 1728;
    static int brushX = 1216;
    static int brushW = 90;
    static int allDoorY = 282;
    static int bigDoorY= 235;
    static int smallDoorW = 160;
    static int smallDoorH = 215;
    static int bigDoorW = 245;
    static int bigDoorH = 265; 
    
    //rectangles for collision into rooms or items
    static Rectangle c1Door = new Rectangle(door1X, allDoorY, smallDoorW, smallDoorH);
    static Rectangle c2Door = new Rectangle(door2X, allDoorY, smallDoorW, smallDoorH);
    static Rectangle officeDoor = new Rectangle(officeDoorX, allDoorY, smallDoorW, smallDoorH);
    static Rectangle exitDoor = new Rectangle (exitDoorX,bigDoorY, bigDoorW, bigDoorH);
    static Rectangle mcDoor = new Rectangle (mcDoorX,allDoorY,smallDoorW,smallDoorH);
    static Rectangle safe = new Rectangle (safeX, allDoorY,smallDoorW,smallDoorH);
    static Rectangle brushArea = new Rectangle (brushX, allDoorY,brushW,smallDoorH);
    static Rectangle mainCharacter = new Rectangle(mcX,mcY,mcW,mcH); 
    
    //determines if player finds the passcode to the phone
    static Boolean passCodeIsKnownCondition1 = false;
    static Boolean passCodeIsKnownCondition2 = false;
    static Boolean phoneIsUnlockable = false;
    static Boolean phoneIsUnlocked = false; 
    
    //endings based on player's choices
    static Boolean characterOneEnding = false; 
    static Boolean characterTwoEnding = false; 
    
    //determines if player has already seen both endings 
    //if so then show the true ending
    static Boolean hasSeenc1Ending = false;
    static Boolean hasSeenc2Ending = false;
    static Boolean trueEnding = false;
    static Boolean playedOnce = false;
    
    //dialogue booleans makes sure the dialogue is shown only once
    static Boolean c1p1 = false; 
    static Boolean hasSeenc1p1 = false;
    static Boolean c2p1 = false; 
    static Boolean hasSeenc2p1 = false;
    static Boolean c1p2 = false;
    static Boolean hasSeenc1p2 = false;
    static Boolean c2p2 = false; 
    static Boolean hasSeenc2p2 = false; 
    static Boolean c1p3 = false; 
    static Boolean hasSeenc1p3 = false;
    static Boolean c2p3 = false;
    static Boolean hasSeenc2p3 = false;
    
    //font properties for drawing strings for dialogue
    static int fontSize = 24; 
    static Font dialogueFont = new Font ("Monospaced", Font.BOLD, fontSize);
    
    //dialogue Lines
    static int dialogueLineNum = 0; 
    static int numOfLine;
    static String textFileName; 
    
    static String [] introLines;
    static String introLine;
    //character1 phase1
    static String [] c1p1Lines;
    static String c1p1Line;
    //character2 phase 1
    static String [] c2p1Lines;
    static String c2p1Line;  
    //character1 phase 2
    static String [] c1p2Lines;
    static String c1p2Line; 
    //character2 phase 2 
    static String [] c2p2Lines;
    static String c2p2Line;
    //character1 phase 3
    static String [] c1p3Lines; 
    static String c1p3Line;
    //character2 phase 3 
    static String [] c2p3Lines;
    static String c2p3Line;
    //ending lines 
    static String [] endingLines;
    static String endingLine;
    //=================================================================================================================
    
    public static void main(String[] args)throws IOException{
        gameWindow = new JFrame("Game Window");
        gameWindow.setSize(WIDTH,HEIGHT);
        gameWindow.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        canvas = new GraphicsPanel();
        //add keylistener, mouseListener and mouseMotionListener to the graphicsPanel
        canvas.addKeyListener(keyListener);  
        canvas.addMouseListener(mouseListener); 
        canvas.addMouseMotionListener(mouseMotionListener); 
        gameWindow.add(canvas); 
        
        //import all the images from images folder 
        try {
            background = ImageIO.read(new File("images/backgroundCombined().jpg"));
            brush = ImageIO.read(new File("images/brush.png"));
            brushZoomUp = ImageIO.read(new File("images/brushZoom.jpg"));
            safeZoomUp = ImageIO.read(new File("images/safe.jpg"));
            instructionsPage = ImageIO.read(new File("images/instructions.jpg"));
            startButton = ImageIO.read(new File("images/start1.jpg"));
            instruButton = ImageIO.read(new File("images/instru1.jpg"));
            backButton = ImageIO.read(new File("images/back1.jpg"));
            intro = ImageIO.read(new File("images/Intro.jpg"));
            character1 = ImageIO.read(new File("images/Character1.png"));
            character2 = ImageIO.read(new File("images/Character2.png"));
            textBox = ImageIO.read(new File("images/Dialogue.png")); 
            office = ImageIO.read(new File("images/office.jpg")); 
            docNote = ImageIO.read(new File("images/DocNote.png"));
            nurseSticky = ImageIO.read(new File("images/NurseSticky.png"));
            bottleNote = ImageIO.read(new File("images/bottleNote.png"));
            phoneLocked = ImageIO.read(new File("images/phoneLocked.png"));
            phoneUnlocked = ImageIO.read(new File("images/phone.png")); 
            calendar = ImageIO.read (new File("images/Calendar.png"));
            phonePasscode = ImageIO.read(new File("images/phonePassCode1.jpg"));
            character1Passcode = ImageIO.read(new File("images/c1PassCode1.jpg"));
            character2Passcode = ImageIO.read(new File("images/c2PassCode1.jpg"));
            c1TalkBackground = ImageIO.read(new File ("images/c1TalkBg.jpg"));
            c2TalkBackground = ImageIO.read(new File("images/c2TalkBg.jpg"));
            mcRoom = ImageIO.read(new File("images/mcRoom.jpg"));
            keypad = ImageIO.read(new File("images/keypad.png"));
            c1EndingImage = ImageIO.read(new File("images/Ending1-2.jpg"));
            c2EndingImage = ImageIO.read(new File("images/Ending2-2.jpg"));
            trueEndingBackground = ImageIO.read(new File("images/TrueEndingBackground.jpg"));
            nurse = ImageIO.read(new File("images/Nurse.png"));
        } catch (IOException ex){}
        
        //moving background
        backgroundW = background.getWidth();
        backgroundH = background.getHeight();
        //intro dialogue lines
        introLines = readDialogue(11,"Intro.txt");
        introLine = displayDialogue(introLines,dialogueLineNum);
        //character1 phase 1 lines 
        c1p1Lines = readDialogue(11,"C1Phase1.txt");
        c1p1Line = displayDialogue(c1p1Lines,dialogueLineNum);
        //character2 phase 1 lines 
        c2p1Lines = readDialogue(11,"C2Phase1.txt");
        c2p1Line = displayDialogue(c2p1Lines,dialogueLineNum);
        //character1 phase 2 lines 
        c1p2Lines = readDialogue(5,"C1Phase2.txt");
        c1p2Line = displayDialogue(c1p2Lines,dialogueLineNum);
        //character2 phase 2 lines 
        c2p2Lines = readDialogue(5,"C2Phase2.txt");
        c2p2Line = displayDialogue( c2p2Lines,dialogueLineNum);
        //character1 phase 3 lines 
        c1p3Lines = readDialogue(11,"C1Phase3.txt");
        c1p3Line = displayDialogue( c1p3Lines ,dialogueLineNum);
        //character2 phase 3 lines 
        c2p3Lines = readDialogue(11,"C2Phase3.txt");
        c2p3Line = displayDialogue( c2p3Lines,dialogueLineNum);
        //true ending lines 
        endingLines = readDialogue(10,"Ending.txt");
        endingLine = displayDialogue( endingLines,dialogueLineNum);
        //character sprite
        for (int i=0; i<9;i++){
            try{
                mcPic[i]= ImageIO.read(new File("images/mc" + Integer.toString(i)+ ".png"));
            } catch (IOException ex){} 
        }
        //random title page
        randTitle = (int)(Math.random()*4)+1; 
        try{
            title = ImageIO.read(new File("images/title" + Integer.toString(randTitle)+ ".jpg"));
        }catch (IOException ex){}
        gameWindow.setVisible(true);
        runGameLoop();
    }//main
    
    //=================================================================================================================
    public static void runGameLoop()throws IOException{
        while (true) {
            gameWindow.repaint();
            try  {Thread.sleep(50);} catch(Exception e){}
            // select main character's picture    
            if (mcState == "standing left"){
                mcPicNum = 0;
            } else if (mcState == "standing right"){
                mcPicNum = 4;                              
            } else if (mcState == "walking left"){
                mcPicNum = nextLeftPic[mcPicNum]; 
            } else if (mcState == "walking right"){                    
                mcPicNum = nextRightPic[mcPicNum];  
            } else if (mcState == "looking up"){
                mcPicNum = 8;
            }
            //when player finds both conditions of to know the phone passcode give player option to unlock it 
            if (passCodeIsKnownCondition1 && passCodeIsKnownCondition2){
                phoneIsUnlockable = true;  
            }
            //when player finds all four numbers give play option to enter the third phase and speak to the characters
            if (num1IsKnown && num2IsKnown &&num3IsKnown &&num4IsKnown ){
                phase3Flag = true; 
                phase2Flag = false;
            }
            //lets player chose one exiting passcode after speaking to both characters 
            if(hasSeenc1p3 && hasSeenc2p3){
                exitOption= true;
            }
            //call method to determine if player has already seen both endings
            writeHasSeenEnding(playedOnce,characterOneEnding,characterTwoEnding);
            //call method to determine if player should be shown the true ending
            trueEnding = readTrueEnding(playedOnce);
        } 
    }//run game loop
    
    //=================================================================================================================
    
    static class GraphicsPanel extends JPanel{
        public GraphicsPanel(){
            setFocusable(true);
            requestFocusInWindow();
        }
        public void paintComponent(Graphics g){ 
            super.paintComponent(g); //required 
            //main game window title page with start button and instructions button
            if(titleDisplay){
                g.drawImage(title,TOP,LEFT,this); 
                g.drawImage(startButton,allButtonX,startY,this);
                g.drawImage(instruButton,allButtonX,instruY,this);
            }
            //instructions page with instructions and a back button to go back to the title page
            if(instructions){
                g.drawImage(instructionsPage,TOP,LEFT,this);
                g.drawImage(backButton,backX,backY,this); 
            }
            //intro Animation intro background and intro dialogue display
            if(introAnimation){
                g.drawImage(intro,TOP,LEFT,this); 
                g.setColor(Color.white);
                g.setFont(dialogueFont); 
                g.drawString(introLine,300,300);
            }
            //main game screen with hallway background and moving character sprite
            if(gamePlay){
                g.drawImage(background,backgroundX,backgroundY,this);
                g.drawImage(mcPic[mcPicNum],mcX,mcY,this);
                g.drawImage(brush,backgroundX,backgroundY,this);
            }
            //character 1 phase 1 draws character1 and shows dialogue 
            if (c1p1 && !hasSeenc1p1){
                g.drawImage(c1TalkBackground,TOP,LEFT,this);
                g.drawImage(character1,TOP,LEFT,this);
                g.drawImage(textBox,TOP,LEFT,this);
                g.setColor(Color.white);
                g.setFont(dialogueFont); 
                g.drawString(c1p1Line,50,500);
            }
            //character 2 phase 1 draws character2 and shows dialogue 
            if(c2p1&& !hasSeenc2p1){
                g.drawImage(c2TalkBackground,TOP,LEFT,this);
                g.drawImage(character2,TOP,LEFT,this);
                g.drawImage(textBox,TOP,LEFT,this);
                g.setColor(Color.white);
                g.setFont(dialogueFont); 
                g.drawString(c2p1Line,50,500);
            }
            //character 1 phase 2 draws character1 and shows dialogue 
            if(c1p2){
                g.drawImage(c1TalkBackground,TOP,LEFT,this);
                g.drawImage(character1,TOP,LEFT,this);
                g.drawImage(textBox,TOP,LEFT,this);
                g.setColor(Color.white);
                g.setFont(dialogueFont); 
                g.drawString(c1p2Line,50,500);
            }
            //character 2 phase 2 draws character2 and shows dialogue 
            if(c2p2){
                g.drawImage(c2TalkBackground,TOP,LEFT,this);
                g.drawImage(character2,TOP,LEFT,this);
                g.drawImage(textBox,TOP,LEFT,this);
                g.setColor(Color.white);
                g.setFont(dialogueFont); 
                g.drawString(c2p2Line,50,500);
            }
            //character 1 phase 3 draws character1 and shows dialogue 
            if(c1p3){
                g.drawImage(c1TalkBackground,TOP,LEFT,this);
                g.drawImage(character1,TOP,LEFT,this);
                g.drawImage(textBox,TOP,LEFT,this);
                g.setColor(Color.white);
                g.setFont(dialogueFont); 
                g.drawString(c1p3Line,50,500);
            }
            //character 2 phase 3 draws character2 and shows dialogue 
            if(c2p3){
                g.drawImage(c2TalkBackground,TOP,LEFT,this);
                g.drawImage(character2,TOP,LEFT,this);
                g.drawImage(textBox,TOP,LEFT,this);
                g.setColor(Color.white);
                g.setFont(dialogueFont); 
                g.drawString(c2p3Line,50,500);
            }
            //office room draws office room 
            //draws zoom up of items if clicked 
            if(officeRoom){
                g.drawImage(office,TOP,LEFT,this);
                g.drawImage(backButton,backX,backY,this); 
                if (drawDocNote)
                    g.drawImage(docNote,TOP,LEFT,this);
                if (drawNurseSticky)
                    g.drawImage(nurseSticky,TOP,LEFT,this);
                if (drawBottleNote)
                    g.drawImage(bottleNote,TOP,LEFT,this);
                if (drawCalendar)
                    g.drawImage(calendar,TOP,LEFT,this);
                if (drawPhone && !phoneIsUnlockable){
                    g.drawImage(phoneLocked,TOP,LEFT,this);
                }else if (drawPhone && phoneIsUnlockable){
                    g.drawImage(phoneLocked,TOP,LEFT,this);
                    g.drawImage(phonePasscode,allButtonX, instruY,this);
                }
                if (phoneIsUnlocked)
                    g.drawImage(phoneUnlocked,TOP,LEFT,this);
            }
            //exit door draws exit keypad 
            if (exit){
                g.drawImage(keypad,TOP,LEFT,this);
            }
            //draws exit keypad and the two passcodes given by the two characters 
            if(drawExitOption){
                g.drawImage(keypad,TOP,LEFT,this);
                g.drawImage(character1Passcode,allButtonX,startY,this);
                g.drawImage(character2Passcode,allButtonX,instruY,this);
            }
            //ending for chosing character1's passcode 
            if (characterOneEnding){
                g.drawImage(c1EndingImage,TOP,LEFT,this);
                g.setColor(Color.black);
                g.setFont(dialogueFont); 
                g.drawString("1/2",300,300);
                playedOnce = true;
            }
            //ending for chosing character2's passcode 
            if (characterTwoEnding){
                g.drawImage(c2EndingImage,TOP,LEFT,this);
                g.setColor(Color.black);
                g.setFont(dialogueFont); 
                g.drawString("1/2",300,300);
                playedOnce = true;
            }
            //draws zoom up of main character's room
            if(drawMcRoom){
                g.drawImage(mcRoom,TOP,LEFT,this);
            }
            //draws zoom up of the brush 
            if (drawBrush){
                g.drawImage(brushZoomUp,TOP,LEFT,this); 
            }
            //draws zoom up of the safe in the hallway
            if (drawSafe){
                g.drawImage(safeZoomUp,TOP,LEFT,this); 
            }
            //if player has already seen both endings display true ending 
            if (trueEnding){
                g.drawImage(trueEndingBackground ,TOP,LEFT,this);
                g.drawImage(nurse,TOP,LEFT,this);
                g.drawImage(textBox,TOP,LEFT,this);
                g.setColor(Color.white);
                g.setFont(dialogueFont); 
                g.drawString(endingLine,50,500);
            }
            //ending page of the entire game 
            if (endGame){
                g.drawImage(intro,TOP,LEFT,this); 
                g.setColor(Color.white);
                g.setFont(dialogueFont); 
                g.drawString("Thanks for playing!",300,300);
            }
        }
    }
    //=================================================================================================================
    static class MyKeyListener implements KeyListener{      
        public void keyPressed(KeyEvent e){
            int key = e.getKeyCode();
            //advancing dialogue in the intro section 
            if(key == KeyEvent.VK_SPACE && introAnimation && dialogueLineNum <10){
                dialogueLineNum = dialogueLineNum+1;
                introLine = displayDialogue(introLines,dialogueLineNum);
            }else if (key == KeyEvent.VK_SPACE && introAnimation && dialogueLineNum >= 10){
                introAnimation = false; 
                gamePlay = true;
            }
            //triggering character 1 phase 1 dialogue
            if( key == KeyEvent.VK_UP && mainCharacter.intersects(c1Door) && gamePlay && !hasSeenc1p1){
                c1p1=true;
                gamePlay = false;
                dialogueLineNum = 0;
            }
            //advancing character 1 phase 1 dialogue
            if (key== KeyEvent.VK_SPACE && c1p1 && dialogueLineNum <10 && mainCharacter.intersects(c1Door) ){
                dialogueLineNum = dialogueLineNum+1;
                c1p1Line = displayDialogue(c1p1Lines,dialogueLineNum);
                
            }else if (key == KeyEvent.VK_SPACE && c1p1 && dialogueLineNum >=10 && mainCharacter.intersects(c1Door)){
                c1p1 = false;  
                gamePlay =true;
                hasSeenc1p1= true; 
            }
            //triggering character 2 phase 1 dialogue
            if(key == KeyEvent.VK_UP && mainCharacter.intersects(c2Door) && gamePlay && !hasSeenc2p1){
                c2p1=true;
                gamePlay = false;
                dialogueLineNum = 0;
            }
            //advancing character 2 phase 1 dialogue
            if (key== KeyEvent.VK_SPACE && c2p1 &&dialogueLineNum <10){
                dialogueLineNum= dialogueLineNum +1;
                c2p1Line = displayDialogue(c2p1Lines,dialogueLineNum);
                
            }else if (key == KeyEvent.VK_SPACE && c2p1 && dialogueLineNum >=10){
                c2p1 = false;  
                gamePlay =true;
                hasSeenc2p1= true; 
            }
            //entering the office room
            if(key == KeyEvent.VK_UP && mainCharacter.intersects(officeDoor) && gamePlay && hasSeenc1p1 && hasSeenc2p1){
                officeRoom = true;
                gamePlay = false;
            }
            //triggering to draw a zoom up of main character's room
            if (key == KeyEvent.VK_UP && mainCharacter.intersects(mcDoor) && gamePlay){
                drawMcRoom = true;
            }else if (key == KeyEvent.VK_SPACE && mainCharacter.intersects(mcDoor) && gamePlay){
                drawMcRoom = false;
            }
            //triggering to draw a zoom up of brush
            if (key == KeyEvent.VK_UP && mainCharacter.intersects(brushArea) && gamePlay){
                drawBrush = true;
            }else if (key == KeyEvent.VK_SPACE && mainCharacter.intersects(brushArea) && gamePlay){
                drawBrush = false;
            }
            //triggering to draw a zoom up of safe
            if (key == KeyEvent.VK_UP && mainCharacter.intersects(safe) && gamePlay){
                drawSafe = true;
            }else if (key == KeyEvent.VK_SPACE && mainCharacter.intersects(safe) && gamePlay){
                drawSafe = false;
            }
            //triggering chararcter1 phase2 dialogue
            if( key == KeyEvent.VK_UP && mainCharacter.intersects(c1Door) && gamePlay && !hasSeenc1p2 && phase2Flag){
                c1p2=true;
                gamePlay = false;
                dialogueLineNum = 0;
            }
            //advancing character 1 phase 2 dialogue 
            if (key== KeyEvent.VK_SPACE && c1p2 && dialogueLineNum <4 ){
                dialogueLineNum = dialogueLineNum +1;
                c1p2Line = displayDialogue(c1p2Lines,dialogueLineNum);
            }else if (key == KeyEvent.VK_SPACE && c1p2 && dialogueLineNum >=4 && mainCharacter.intersects(c1Door)){
                c1p2 = false;  
                gamePlay =true;
                hasSeenc1p2= true; 
            }
            //triggering chararcter2 phase2 dialogue
            if(key == KeyEvent.VK_UP && mainCharacter.intersects(c2Door) && gamePlay && !hasSeenc2p2 && phase2Flag){
                c2p2=true;
                gamePlay = false;
                dialogueLineNum = 0;
            }
            //advancing character 2 phase 2 dialogue 
            if (key== KeyEvent.VK_SPACE && c2p2 && dialogueLineNum <4){
                dialogueLineNum = dialogueLineNum +1;
                c2p2Line = displayDialogue( c2p2Lines,dialogueLineNum);
                
            }else if (key == KeyEvent.VK_SPACE && c2p2 && dialogueLineNum >=4){
                c2p2 = false;
                passCodeIsKnownCondition1 = true;
                gamePlay =true;
                hasSeenc2p2= true; 
            }
            //triggering character1 phase 3 dialogue
            if( key == KeyEvent.VK_UP && mainCharacter.intersects(c1Door) && gamePlay && !hasSeenc1p3 && phase3Flag){
                c1p3=true;
                gamePlay = false;
                dialogueLineNum = 0;
            }
            //advancing character 1 phase 3 dialogue 
            if (key== KeyEvent.VK_SPACE && c1p3 && dialogueLineNum <10 ){
                dialogueLineNum = dialogueLineNum +1;
                c1p3Line = displayDialogue( c1p3Lines ,dialogueLineNum);
            }else if (key == KeyEvent.VK_SPACE && c1p3 && dialogueLineNum >=10 && mainCharacter.intersects(c1Door)){
                c1p3 = false;  
                gamePlay =true;
                hasSeenc1p3= true; 
            }
            //triggering character 2 phase 3 dialogue
            if(key == KeyEvent.VK_UP && mainCharacter.intersects(c2Door) && gamePlay && !hasSeenc2p3 && phase3Flag){
                c2p3=true;
                gamePlay = false;
                dialogueLineNum = 0;
            }
            //advancing character 2 phase 3 dialogue 
            if (key== KeyEvent.VK_SPACE && c2p3 && dialogueLineNum <10){
                dialogueLineNum =dialogueLineNum +1;
                c2p3Line = displayDialogue( c2p3Lines,dialogueLineNum);
            }else if (key == KeyEvent.VK_SPACE && c2p3 && dialogueLineNum>=10){
                c2p3 = false;
                gamePlay =true;
                hasSeenc2p3= true; 
            }
            //advancing ending dialogue
            if (key== KeyEvent.VK_SPACE && trueEnding && dialogueLineNum < 9 ){
                dialogueLineNum =dialogueLineNum+1;
                endingLine = displayDialogue( endingLines,dialogueLineNum);
                //ending the game entirely 
            }else if (key == KeyEvent.VK_SPACE && trueEnding && dialogueLineNum >=9 ){
                trueEnding = false;
                endGame = true;
            }
            //triggering to draw keypad at the exit door 
            if(key == KeyEvent.VK_UP && mainCharacter.intersects(exitDoor) && gamePlay&& !exitOption){
                exit = true;
                gamePlay = false;
            }else if (key == KeyEvent.VK_SPACE && mainCharacter.intersects(exitDoor) && !exitOption){
                exit = false;
                gamePlay = true;
                //giving the player options to chose once the passcode from each character is known 
            }else if (key == KeyEvent.VK_UP && mainCharacter.intersects(exitDoor) && gamePlay && exitOption){
                drawExitOption = true;
            }else if (key == KeyEvent.VK_SPACE && mainCharacter.intersects(exitDoor) && gamePlay && exitOption){
                drawExitOption = false;
            }
            //exit zoom ups in the office room 
            if (drawDocNote || drawNurseSticky||drawBottleNote||drawCalendar||drawPhone||phoneIsUnlocked){
                if (key== KeyEvent.VK_SPACE) {
                    drawDocNote = false;
                    drawNurseSticky = false;
                    drawBottleNote = false;
                    drawCalendar = false;
                    drawPhone = false;
                    phoneIsUnlocked = false;
                }
            }
            //moving background, character sprite and rectangles for collision 
            if (key == KeyEvent.VK_LEFT && backgroundX <= 0&&gamePlay){
                // move the background to the left   
                // move the rectangles along with the background for collision 
                backgroundX = backgroundX + stepX;
                door1X= door1X + stepX;
                c1Door.setLocation(door1X,allDoorY);
                door2X= door2X + stepX;
                c2Door.setLocation(door2X,allDoorY);
                officeDoorX = officeDoorX + stepX;
                officeDoor.setLocation(officeDoorX,allDoorY);
                exitDoorX= exitDoorX + stepX;
                exitDoor.setLocation(exitDoorX,bigDoorY);
                mcDoorX = mcDoorX + stepX;
                mcDoor.setLocation(mcDoorX,allDoorY); 
                safeX = safeX + stepX;
                safe.setLocation(safeX,allDoorY);
                brushX= brushX + stepX;
                brushArea.setLocation(brushX,allDoorY);
                if (mcState == "standing left"){
                    mcState = "walking left";
                } else if (mcState == "standing right"){
                    mcState = "standing left";
                } else if (mcState == "walking left"){
                    //no action
                } else if (mcState == "walking right"){
                    mcState = "standing right";
                } else if (mcState == "looking up"){
                    mcState = "standing left";
                }
            } else if (key == KeyEvent.VK_RIGHT && backgroundX >= RIGHT - backgroundW&&gamePlay){
                // move the background to the right
                // move the rectangles along with the background for collision 
                backgroundX = backgroundX - stepX;
                door1X = door1X - stepX;
                c1Door.setLocation(door1X,allDoorY);
                door2X= door2X - stepX;
                c2Door.setLocation(door2X,allDoorY);
                officeDoorX = officeDoorX - stepX;
                officeDoor.setLocation(officeDoorX,allDoorY);
                exitDoorX= exitDoorX - stepX;
                exitDoor.setLocation(exitDoorX,bigDoorY);
                mcDoorX = mcDoorX - stepX;
                mcDoor.setLocation(mcDoorX,allDoorY); 
                safeX = safeX - stepX;
                safe.setLocation(safeX,allDoorY);
                brushX= brushX - stepX;
                brushArea.setLocation(brushX,allDoorY);
                if (mcState == "standing left"){
                    mcState = "standing right";
                } else if (mcState == "standing right"){
                    mcState = "walking right";
                } else if (mcState == "walking left"){
                    mcState = "standing left";
                } else if (mcState == "walking right"){
                    // no action
                } else if (mcState == "looking up"){
                    mcState = "standing right";
                }
            }//moving background, character sprite and rectangles for collision 
            if(key == KeyEvent.VK_UP){
                mcState = "looking up";
            }
        }
        public void keyReleased(KeyEvent e){
            //stop the character sprite from moving once the left and right arrow keys are released 
            if (mcState == "walking right"){
                mcState = "standing right";
            }else if (mcState == "walking left"){
                mcState = "standing left";
            }
        }//keyReleased
        public void keyTyped(KeyEvent e){
        }        
    } // MyKeyListener class
    //=================================================================================================================
    
    static class MyMouseListener implements MouseListener{
        public void mouseClicked(MouseEvent e){
            //no action
        }
        public void mousePressed(MouseEvent e){ 
            int mouseX = e.getX();
            int mouseY = e.getY();
            //mouse clicking the start game button 
            if (mouseX > allButtonX && mouseX < buttonW+allButtonX && mouseY > startY && mouseY < startY+buttonH && titleDisplay){
                titleDisplay = false; 
                introAnimation = true; 
            }
            //mouse clicking on the instructions button to enter instructions page 
            else if (mouseX>allButtonX && mouseX<buttonW+allButtonX && mouseY >instruY && mouseY <instruY+buttonH && titleDisplay){
                titleDisplay = false; 
                instructions = true;
            }
            //mouse clicking on the back button from the instructions page to return to game title page 
            if (mouseX > backX && mouseX < buttonW + backX && mouseY > backY && mouseY < backY+buttonH && instructions){
                instructions = false;
                titleDisplay = true; 
            }
            //mouse clicking the back button from the office room to return to the main game hallway
            if (mouseX > backX && mouseX < buttonW + backX && mouseY > backY && mouseY < backY+buttonH && officeRoom){
                officeRoom= false; 
                gamePlay = true; 
            }
            //mouse clicking on the items in the office room to trigger a zoom up 
            //with each item the player learns another to the final passcode 
            //once the player clicked on the phone drawer it triggers the second phase of dialogue with the characters 
            if (mouseX > docNoteX && mouseX< docNoteX + docNoteW && mouseY > docNoteY&&mouseY <docNoteY+docNoteH&& officeRoom){
                drawDocNote = true;
                num1IsKnown = true;
            }else if(mouseX > nurseStickyX && mouseX< nurseStickyX + nurseStickyW && mouseY > nurseStickyY&&mouseY <nurseStickyY + nurseStickyH&& officeRoom){
                drawNurseSticky= true; 
                num2IsKnown = true;
            }else if (mouseX > bottleNoteX && mouseX< bottleNoteX + bottleNoteW && mouseY > bottleNoteY&&mouseY <bottleNoteY + bottleNoteH&& officeRoom){
                drawBottleNote = true;
                num3IsKnown = true;
            }else if (mouseX > calendarX && mouseX< calendarX + calendarW && mouseY > calendarY&&mouseY <calendarY + calendarH&& officeRoom){
                drawCalendar= true;
                passCodeIsKnownCondition2 = true;
            } else if (mouseX > phoneDrawerX && mouseX< phoneDrawerX + phoneDrawerW && mouseY > phoneDrawerY&&mouseY <phoneDrawerY + phoneDrawerH&& officeRoom){
                drawPhone = true;
                phase2Flag = true;
            }
            //to unlock phone 
            //the two conditions to knowing the passcode for the phone is looking at the calendar and speaking to 
            //character two during the second stage
            if(mouseX>allButtonX && mouseX<buttonW+allButtonX && mouseY >instruY && mouseY <instruY+buttonH && phoneIsUnlockable){
                phoneIsUnlocked = true;
                num4IsKnown = true;
            }
            //once the player triggered all four flags for knowing the numbers to the final code 
            //it triggers the third phase of dialogue 
            
            //chosing passcode to try which determines the ending the player gets
            //character one ending 
            if (mouseX > allButtonX && mouseX < buttonW+allButtonX && mouseY > startY && mouseY < startY+buttonH && drawExitOption){
                characterOneEnding = true;
                hasSeenc1Ending = true;
                drawExitOption = false;
                dialogueLineNum = 0;
                
                //character two ending 
            }else if (mouseX>allButtonX && mouseX<buttonW+allButtonX && mouseY >instruY && mouseY <instruY+buttonH && drawExitOption){
                characterTwoEnding = true;
                hasSeenc2Ending = true;
                drawExitOption = false;
                dialogueLineNum = 0;
            }
            
        }//mousePressed
        public void mouseReleased(MouseEvent e){
            //no action
        }//mouseReleased 
        public void mouseEntered(MouseEvent e){
            //no action
        }//mouseEntered
        public void mouseExited(MouseEvent e){
            //no action
        }//mouseExited 
    }//MyMouseListener
    
    //=================================================================================================================
    static class MyMouseMotionListener implements MouseMotionListener{
        public void mouseMoved(MouseEvent e){ 
            int mouseX = e.getX();
            int mouseY = e.getY();
            //mouse hovers start button causing it to change colors 
            if (mouseX > allButtonX && mouseX < buttonW+allButtonX && mouseY > startY && mouseY < startY+buttonH && titleDisplay){
                try {
                    startButton = ImageIO.read(new File("images/start2.jpg"));
                } catch (IOException ex){}
            }else {
                try {
                    startButton = ImageIO.read(new File("images/start1.jpg"));  
                } catch (IOException ex){}
            }
            //mouse hovers instructions button causing it to change colors 
            if (mouseX>allButtonX && mouseX<buttonW+allButtonX && mouseY >instruY && mouseY <instruY+buttonH && titleDisplay){
                try {
                    instruButton = ImageIO.read(new File("images/instru2.jpg"));
                } catch (IOException ex){}
            }else {
                try {
                    instruButton = ImageIO.read(new File("images/instru1.jpg"));
                } catch (IOException ex){}
            }
            //mouse hovers back button(on instructions page) causing it to change colors 
            if (mouseX > backX && mouseX < buttonW+backX && mouseY > backY && mouseY < backY+buttonH && instructions){
                try {        
                    backButton = ImageIO.read(new File("images/back2.jpg"));
                } catch (IOException ex){}
            }else {
                try {        
                    backButton = ImageIO.read(new File("images/back1.jpg"));
                } catch (IOException ex){}
            }
            //mouse hovers back button(in office ) causing it to change colors 
            if (mouseX > backX && mouseX < buttonW+backX && mouseY > backY && mouseY < backY+buttonH && officeRoom){
                try {        
                    backButton = ImageIO.read(new File("images/back2.jpg"));
                } catch (IOException ex){}
            }else {
                try {        
                    backButton = ImageIO.read(new File("images/back1.jpg"));
                } catch (IOException ex){}
            }
            //mouse hovers phone passcode button causing it to change colors 
            if(mouseX>allButtonX && mouseX<buttonW+allButtonX && mouseY >instruY && mouseY <instruY+buttonH && phoneIsUnlockable){
                try {        
                    phonePasscode = ImageIO.read(new File("images/phonePassCode2.jpg"));
                } catch (IOException ex){}
            }else {
                try {        
                    phonePasscode = ImageIO.read(new File("images/phonePassCode1.jpg"));
                } catch (IOException ex){}
            }
            //mouse hovers character1 passcode button causing it to change colors             
            if (mouseX > allButtonX && mouseX < buttonW+allButtonX && mouseY > startY && mouseY < startY+buttonH && drawExitOption){
                try {        
                    character1Passcode = ImageIO.read(new File("images/c1PassCode2.jpg"));
                } catch (IOException ex){}
            }else{
                try {        
                    character1Passcode = ImageIO.read(new File("images/c1PassCode1.jpg"));
                } catch (IOException ex){}
            } 
            //mouse hovers character2 passcode button causing it to change colors             
            if (mouseX>allButtonX && mouseX<buttonW+allButtonX && mouseY >instruY && mouseY <instruY+buttonH && drawExitOption){
                try {        
                    character2Passcode = ImageIO.read(new File("images/c2PassCode2.jpg"));
                } catch (IOException ex){}
            }else{
                try {        
                    character2Passcode = ImageIO.read(new File("images/c2PassCode1.jpg"));
                } catch (IOException ex){}
            } 
            
        }//motion listener 
        public void mouseDragged(MouseEvent e){
            //no action
        }//mouseDragged
    }//MyMouseMotionListener
    
    //=================================================================================================================
    //method that reads dialogue from textfile 
    public static String[] readDialogue(int numOfLine, String textFileName)throws IOException{
        String [] dialogue = new String [numOfLine];
        File lines = new File("textfile/"+textFileName);
        Scanner textIn1 = new Scanner(lines);  
        for (int i = 0;  i <numOfLine; i ++){
            dialogue[i] = textIn1.nextLine();
        }
        textIn1.close();     
        return dialogue;
    }
    //method that reads the individual lines 
    public static String displayDialogue(String[] dialogue, int dialogueLineNum){
        String dialogueThisLine;
        dialogueThisLine = dialogue[dialogueLineNum];
        return dialogueThisLine;
    }
    
    //=================================================================================================================
    //method determines if the player has already seen both ending by writing in a text file
    public static void writeHasSeenEnding (Boolean playedOnce,Boolean hasSeenc1Ending,Boolean hasSeenc2Ending)throws IOException{
        File file = new File(HasSeenEnding);
        if (!file.exists()) {
            file.createNewFile();
        }
        FileWriter hasSeenEnding = new FileWriter(HasSeenEnding, true);
        BufferedWriter out = new BufferedWriter(hasSeenEnding);
        if (playedOnce && hasSeenc1Ending)
            out.write("One");
        else if(playedOnce && hasSeenc2Ending)
            out.write("Two");
        out.close();
    }
    //=================================================================================================================
    //method that determines if player has already seen both endings
    public static Boolean readTrueEnding (Boolean playedOnce) throws IOException{
        Boolean trueEnding = false;
        String seenEnding= "";
        String seenOne = "One";
        String seenTwo = "Two";
        if (playedOnce){
            File ending = new File("HasSeenEnding.txt");
            Scanner textIn8 = new Scanner(ending);
            seenEnding = textIn8.nextLine(); 
            textIn8.close(); 
        }
        if (seenEnding.contains(seenOne) && seenEnding.contains(seenTwo))
            trueEnding = true;
        return trueEnding; 
    }
} //ComSciFinalProject
