 two-ended BFS Pseudocode model


	public int twoEndedBFS(String beginWord,String endWord,List<String>wordList){

        	Set<String> visited=new HashSet<>(); // store visited string
        	Set<String> beginSet=new HashSet<>(); 
        	Set<String> endSet=new HashSet<>();
        	beginSet.add(beginWord);
        	endSet.add(endWord);
        	int len=1;
		...
		
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


  

