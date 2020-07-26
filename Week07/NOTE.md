   学习笔记
   1. two-ended BFS Pseudocode model


	public int twoEndedBFS(String beginWord,String endWord,List<String>wordList){

        	Set<String> visited=new HashSet<>(); // store visited string
        	Set<String> beginSet=new HashSet<>(); 
        	Set<String> endSet=new HashSet<>();
        	beginSet.add(beginWord);
        	endSet.add(endWord);
        	int len=1;

		
       	Set<String> temp=new HashSet<>();
       	while(!beginSet.isEmpty() && !endSet.isEmpty()){
		
		if(beginSet.size()>endSet.size()){
			swap beginSet and endSet
		}
	
		Set<String> temp=new HashSet<>();
		for（String ele: beginSet){
			new_ele=generate_related_str(ele)
			...
			visitied.add(new_ele)
			temp.add(new_ele)
		}
	
		beginSet=temp;
		len++;	
        }
        return 0;
	}


  
  2. word-search-ii
    
    class Solution {

    HashSet<String> res=new HashSet<>();

    public List<String> findWords(char[][] board, String[] words) {

        WordTrie trie=new WordTrie();

		// store root position in Trie

        Trie root = trie.root;

        for(String word:words){

            trie.insert(word);

        }



        int m = board.length;

        int n = board[0].length;

        boolean[][] visited=new boolean[m][n];

        for(int i=0;i<m;i++){

            for(int j=0;j<n;j++){

                find(i,j,visited,board,m,n,root);

            }

        }

        return new LinkedList<>(res);





    }



    private void find(int i, int j, boolean[][] visited, char[][] board, int m, int n, Trie trie) {

		//terminator

        if(i<0 || i>=m || j<0 || j>=n || visited[i][j])

            return;

        trie = trie.next[board[i][j] - 'a'];

        if(trie==null){

            return;

        }

        if(trie.isEnd){

            res.add(trie.val);

        }

		

		//current level

        visited[i][j]=true;



		// drill down

        int[] row={-1,0,1,0};

        int[] col={0,-1,0,1};

        for(int tmp=0;tmp<4;tmp++){

            find(i+row[tmp],j+col[tmp],visited,board,m,n,trie);

        }

		

		//revert status

        visited[i][j]=false;



    }





    public class WordTrie{

        Trie root=new Trie();



        public void insert(String word){

            Trie curr=root;

            char[] chars = word.toCharArray();

            for (char aChar : chars) {

                if(curr.next[aChar - 'a']==null) {

                    curr.next[aChar - 'a'] = new Trie();

                    curr = curr.next[aChar - 'a'];

                }else

                    curr=curr.next[aChar - 'a'];

            }

            curr.isEnd=true;

            curr.val=word;

        }





    }

    public class Trie{

        boolean isEnd=false;

        Trie[] next=new Trie[26];

        String val;

        public Trie(){}

    }

    }



	
Time complexity：O(m*n), m=total row count in board, n=total column count in board. Worst case is O(m*n*4^k) when it iterates all characters for a certain string in array words 

Space complexity：O(mn+26*X), X=total character counts for each string in array words

