# TicTacToe
This is the usual Tic tac Toe for two players implemented on C language.

Below is the code for the Tic Tac Toe 
      
      #include<stdio.h>
	int getInput()
	{
		int n;
		scanf(" %d",&n);
		if(n<10&&n>0)
		{
			return n;
		}
		else
		{
			printf("\n\t\t====Enter a value from the Available positions"
			" listed above====");
			   n=getInput();
			   return n;
		}
	}
	int winCheck(int *player,int size)
	{
		int winCombo[8][3]={
		{1,2,3},{1,4,7},{1,5,9},{2,5,8},{3,5,7},{3,6,9},{4,5,6},{7,8,9}};
		int a,i,j,count;
		for(a=0;a<8;a++)
		{
			count=0;
			for(i=0;i<3;i++)
			{
				for(j=0;j<size;j++)
				{
					if(winCombo[a][i]==player[j])
					{
						count++;
					}
					if(count==3)
					{
			       return 1;
			       break;
					}
				}
			}
		}
		return 0;
	}
	int check(int *chk)
	{
		int n,j;
	    n=getInput();
		for(j=0;j<9;j++)
		{
			if(chk[j]==n)
			{
				printf("\n The position you ent"
				"ered => (%d) is filled,enter a value" 
				" from the available positions listed above....",n);
				n=check(chk);
				break;
			}
		}
		chk[n]=n;
		return n;
	}
	void display(char * count,int *chk,int win,int loc)
	{
		int i;
		printf("\t\t     Tic Tac Toe ");
		printf("\n\t============================================ ");
		printf("\n\t\t     Player 1 : X ");
		printf("\n\t\t     Player 1 : O ");
	    printf("\n\t\t===================== ");
	    printf("\n\t\t||  %c  || %c  || %c  || ",count[1],count[2],count[3]);
	    printf("\n\t\t===================== ");
	    printf("\n\t\t||  %c  || %c  || %c  || ",count[4],count[5],count[6]);
	    printf("\n\t\t===================== ");
	    printf("\n\t\t||  %c  || %c  || %c  || ",count[7],count[8],count[9]);
	    printf("\n\t\t===================== ");
	    printf("\n\n\tAvailable positions : ");
		for(i=1;i<=9;i++)
		{
			if(chk[i]==0)
			{
				printf("%d ",i);
			}
		}
	    if(win==1)
	    {
	    printf("\n\t\t\t========GAME OVER============= ");
	    if(loc%2!=0)
	    {
		printf("\n\t\t========Player 1 has won the game============= ");
		}
		else
		{
			printf("\n\t\t========Player 2 has won the game============= ");
		}
	    }

		else if(win==2)
		{
			printf("\n\t\t\t========GAME OVER=============");
			printf("\n\t\t\t=======Match Drawn============");
		}
	}
	int main()
	{
		char count[10]={'0'};
		int player1[5],player2[4];
		int chk[10]={0};
		static int i=1,p1=0,p2=0,win;
		int n,d;
		display(count,chk,win,i);
		while(i<=9)
		{
		printf("\n\n\tPlayer 1's turn,Enter your position..");
		d=check(chk);
		player1[p1]=d;
		p1++;
		count[d]='X';
		if(i>4)
		{
		win=winCheck(player1,p1);
	    }
		system("cls");
		display(count,chk,win,i);
		if(win==1)
		{
			break;
		}
			if(i==9)
		{
			win=2;
			system("cls");
		    display(count,chk,win,i);
		}
		++i;
		if(i<9)
	    {
		printf("\n\n\tPlayer 2's turn,Enter your position..");
		d=check(chk);
		player2[p2]=d;
		p2++;
		count[d]='O';
		if(i>=4)
		{
		win=winCheck(player2,p2);
	    }
		system("cls");
		display(count,chk,win,i);
		if(win==1)
		{
			break;
		}
		++i;
	    }
	    }
	}
