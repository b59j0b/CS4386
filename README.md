java cCS4386 AI Game Programming (Semester B, 2024-2025)
Assignment 1:
Trap Gomoku
Set by CS4386 TA Team
Tournament1 Deadline:
Friday 28 February 2025 23:59
Tournament2 Deadline:
Wednesday 12 March 2025 23:59
This assignment is worth
15 % (fifteen percent)
of the overall course mark
Overview
1 Introduction
2 Marking Scheme
3 The Trap Gomoku Game
4 Online Judgment Platform
5 Requirements
6 QA
7 Academic Honesty
Appendix: Sample submission code
1 Introduction
Your task is to develop an AI program capable of playing the Trap Gomoku game.
You may implement your AI using algorithms covered in class or explore other
strategies. The implementation can be done in Python, Java, C, or C++.
To test and evaluate your AI, you will submit your code to an online AI game
judgment platform. The platform provides three preset AI opponents of varying
difficulty, allowing you to test your AI an unlimited number of times by
competing against them. Testing and refining your AI strategy against the three
preset AIs on the platform will help you improve your AI before competing in the
tournaments, where each participant will compete against every other
participant.
2 Marking Scheme
Item Due Mark
Tournament1 (students vs. students)
Tournament2 (students vs. students)
Students vs. Preset AIs
Report
28th Feb 23:59
12th Mar 23:59
12th Mar 23:59
12th Mar 23:59
20
20
30
30
 Total 100
Your final grade will be based on the following aspects:
● Whether you beat our three preset AIs. If you beat all three preset AIs, you
will get 30 points (10 points for each AI). The battle against each preset AI
is divided into two games: first player and second player. If you win only
one game, you will get 5 points.
● Your ranking in tournaments. We will schedule two tournaments, where
each participant will compete against every other participant once. After
the tournament, you will see where your AI stands in the rankings. These
rankings are an integral part of your overall assessment.
● In addition to the score from your AI performance, the quality of your
report will also affect the final score. Your report should explain your
1
approach, justify algorithmic choices, and analyze the strengths and
weaknesses of your AI.
3 The Trap Gomoku Game
The Trap Gomoku Game is a strategic board game where two artificial
intelligence (AI) players compete by aligning five of their pieces consecutively in
a straight line (horizontally, vertically, or diagonally) on a 15x15 grid. In addition,
at the beginning of the game, the system will randomly generate 10-15 trap
pieces and make them public to players. If the chess piece you place lands on a
trap, it will devour the piece, and the trap will remain.
Each player takes turns placing their pieces, aiming to align five consecutively in
a straight line. The "X" represents the trap, and the black and gray circles
represent Player 1 and Player 2's pieces, respectively (shown in Figure 1). The
game ends when the grid is filled (no more than 225 moves) and the player who
creates five of their pieces consecutively in a straight line on the grid will be the
winner. Special Case: If the board is full and there is still no line of 5 pieces. Then
the side with the longest connection is judged to be the winner (for example, if
the white chess piece has the longest 4 pieces in a line, and the black chess piece
has the longest 3 pieces in a line, then the white piece wins), otherwise, it is a
draw. You are encouraged to come up with your own strategies to make your AI
make better decisions at each turn. We are excited to see your brilliant ideas and
how they challenge each other!
2
Figure 1. Two instances of the game board
4 Online Judgment Platform
Website URL: http://cs4386.cs.cityu.edu.hk/user/login/
This URL can only be accessed within the CityU campus network. If you want to
use this website outside the campus, please use CityU VPN first.
Register and log in
● You should register using your CityU email.
● You should register using your real name.
● Upon registration, you will be assigned a user ID. Only your ID will be
shown in the ranking.
Submit your code: play against preset AI
Click "Game" in the left column, and then you will see the Trap Gomoku game. In
the game description, there are time and memory constraints for each step.
Please note that exceeding the time or memory limit will result in an automatic
loss. Click "Submit Here" to go to the submission page. The platform provides a
sample algorithm: a random decision AI. You can use this as a reference to
understand the input-output format and game mechanics before implementing
your own strategy. The system will only retain your latest submission, so please
ensure that your last submitted code runs correctly. If you have iterated through
3
multiple versions, it is recommended that you save them locally to avoid losing
previous work.
We have set up three predetermined AI opponents for you to challenge:
"Offensive," "Defensive," and "Random," designated by user IDs 1, 2, and 3,
respectively. You can select the AI you want to compete against by choosing its
ID.
After submitting your code, you will not receive the result immediately. You
need to click refresh to view your game results. To ensure fairness and account
for any advantages or disadvantages of moving first, each AI pairing will consist
of two matches:
● One match where your own AI moves first.
● One match where your opponent moves first.
The results of these matches, along with time and memory usage, will be
updated after each submission.
Check log
You can download the log to view the state of the chessboard at each step after
getting the results. We also provide a visual interface that displays the placement
of each move step by step, making it easier for you to analyze and review your
games.
Tournament and Ranking
The tournament itself takes place the day following the deadline. On this
"competition day," the server will be offline. Your AI's performance will be
evaluated based on its win rate across the matches (If there is a draw, it will not
count as a win). When two participants' AIs have identical win rates, the AI that
used less time to achieve its wins will receive a higher ranking. After the
tournament, e代 写CS4386、Java
代做程序编程语言ach participant can view the match logs of all their games against
other players. Once everyone has reviewed the logs and confirmed no issues, we
will announce the tournament rankings through the ranking page.
4
5 Requirements
Format of the code:
● The answer must include the play_games function as the interface for
online judgment, which is defined as,
C/C++: void play_games(int step, int rival_decision1,int rival_decision2);
Python: play_games(step:int,rival_decision_x:int,rival_decision_y:int)->None
Java: public static void play_games(int step, int rival_decision_x, int
rival_decision_y)->None
● Step indicates the move number in the current game. It starts from
Player A, step=1, then turns to player B, step=2, and then turns to
player A, step=3, …, end of the game.
● That is, player A's step is always odd, and player B's step is even.
Step=0 represents an empty checkerboard for initialization.
● rival_decision_x,y are the opponent’s decisions made in the
previous step, which can help you make better responses.
● You can read the board and save the decision through the read_ckbd and
save_decision functions. MAX_M and MAX_N are the size of the board
(equal to 15 in this game). They are defined in battle_base.
● C/C++: void read_ckbd(int step, int array[MAX_M][MAX_N]);
void save_decision(int x, int y);
● Python: read_ckbd(step:int)->List[List[int]]
save_decision(x:int, y:int)->None
● Java: battle_base.read_ckbd(int step) -> int [MAX_M][MAX_N];
battle_base.save_decision(int x, int y);
● In the array/list returned by read_ckbd, 0 represents the unplayed
area and you can make a decision here. 1 represents player A’s
decisions, 2 represents player B’s decisions, and 3 represents the
traps.
● Note that you must save your decision by calling save_decision in
the play_games function, don’t return anything. Do not try to
rewrite those functions, you just call them. You can read the
previous step of chess before the current step.
● The main function is not allowed in the answer.
● You can use print/printf/cout to print logs to help you debug. They will
be printed in the battle_log.txt.
5
● If you use Java, JVM will occupy memory, resulting in higher memory
usage.
Submission requirements:
● For Python users: python base modules (in sys.modules.keys()): functools,
random, sorted, heapq, collections, etc. are allowed. You are not allowed
to use other packages like numpy, sklearn, etc.
● For C/C++ users: most header files are allowed, even including
,  and .
● For Java users: You cannot use external third-party libraries or other
non-standard Java packages that are not included in the JDK.
● You cannot use some system calls such as change directory, list file,
create file, remove file, etc.
● For all AI programs, we limit the running time and the total memory
usage, which you can find on the website.
● Violation of any of the above will raise an error and cause the game to be
lost.
Requirement for the report:
You should write a report to explain your AI. Describe your algorithm as clearly
as possible. Feel free to use examples and add screenshots or other figures if
they can help better illustrate your method. If you adopt some part of your code
from somewhere, you must fully acknowledge this and provide a reference to
where you obtained the code. You must declare how much of your submitted
code is obtained from someone/somewhere else and how much is indeed
written by you. At the end of your report, include the related references from
where you have gathered useful information in working on your assignment.
You need to submit your source code to the online judgment system and submit
your report to Canvas.
Name your files according to the following format, where XXXXXXXX is the 8
digits of your student ID number:
CS4386-2425B-A1-XXXXXXXX-Report.pdf (should be in PDF format)
6 QA
We will also create a discussion on Canvas. You can ask questions there; the TAs
will check it daily and answer your questions as soon as possible.
6
7 Academic Honesty
We have repeatedly emphasized the importance of academic honesty. Review
the website https://www.cityu.edu.hk/pvdp/ah/index.htm on academic
honesty if needed.
This is an individual assignment so each of you should write your own code. You
should never send any part of your code to your classmate “for his/her
reference” or copy any part of the code from your classmate. You should
obviously understand the code that you submit, and be able to explain your code
when asked.
Make sure that you do not commit any academic dishonest behaviors while
working on this assignment!
7
Appendix: Sample submission code
Python:
import random
from battle_base import read_ckbd, save_decision,MAX_M,MAX_N
def play_games(step:int,rival_decision_x:int,rival_decision_y:int)->None:
 states = read_ckbd(step-1)
 legal_decision = []
 for m in range(MAX_M):
 for n in range(MAX_N):
 if states[m][n]==0: # 0 is unplayed area
 legal_decision.append((m, n))
 # make your decision here
 decision = random.choice(legal_decision)
 save_decision(decision[0], decision[1])
C:
#include 
#include 
#include "battle_base.h"
#define max(a,b) ((a) >= (b) ? (a) : (b))
void play_games(int step, int rival_decision_x,int rival_decision_y) {
 int states[MAX_M][MAX_N]; // Assuming MAX_M and MAX_N are defined board
size
 read_ckbd(step-1, states);
 int legal_decision[MAX_M*MAX_N][2];
 int legal_count = 0;
 for (int m = 0; m 
#include 
#include 
#include "battle_base.h"
void play_games(int step, int rival_decision1,int rival_decision2) {
 int states[MAX_M][MAX_N]; // Assuming MAX_M and MAX_N are defined board
size
 int states_count = 0;
 read_ckbd(step-1, states);
 int legal_decision[MAX_M*MAX_N][2];
 int legal_count = 0;
 for (int m = 0; m  legalDecision = new ArrayList();
 for (int m = 0; m < battle_base.MAX_M; m++) {
 for (int n = 0; n < battle_base.MAX_N; n++) {
 if (states[m][n] == 0) { // 0 is unplayed area
 legalDecision.add(new int[]{m, n});
9
 }
 }
 }
 // Make your decision here
 Random random = new Random();
 int[] decision =
legalDecision.get(random.nextInt(legalDecision.size()));
 battle_base.save_decision(decision[0], decision[1]);
 }
}
10

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
