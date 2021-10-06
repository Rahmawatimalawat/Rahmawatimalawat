PROJECT 2
Rahma Wati Malawat
1313619042

QUESTION 1 : REFLEX AGENT

 temporary = [] --> array kosong untuk tempat penampungan sementara jarak ghost
 states = [childGameState.getPacmanPosition()] --> states mengambil posisi pacman yang terbaru
 temporaryfood = [] --> array kosong untuk menaruh food sementara
 temporary2 = [] --> array kosong untuk tempat penampungan sementara untuk jarak food
 final_score = childGameState.getScore() --> variabel untuk mendapatkan score berdasarkan next state pacman pada currentGameState

  ghostDistance = manhattanDistance(newPos, childGameState.getGhostPositions()[0])
  --> selanjutnya pada permasalahan diquestion 1 saya mengidentifikasi terlebih dahulu posisi/jarak ghost
 menggunakan function manhattanDistance yang akan direturn diantara posis pacman di childGameState dan posisi ghost di childGameState. lalu variabel ghostDistance dimasukkan ke dalam temporary(array kosong).
 selanjutnya saya membuat variabel food_food untuk menampung new food yang mempunyai function asList().
 
 kemudia saya melakukan pengecekan :
  if len(food_food)!=0: --> jika panjang dari foof_food tidak 0, maka terjadi looping :
            for foodPlace in food_food: 
                foodRange = manhattanDistance(newPos, foodPlace)
                temporary2.append(foodRange) --> foodRange akan diappend ke dalam array kosong yaitu temporary2
                
            temporaryfood.append(min(temporary2)) -->mereturn the smallest item pada temporary2 diappend ke dalam temporaryfood dan diulang
        temporary2.clear()    --> kosongkan temporary2

minimalGhost = min(temporary)
selanjutnya saya mengidentifikasi jarak terkecil antara pacman dan ghost dengan fungsi min().

 if newScaredTimes[0] > 0: --> "newScaredTimes holds the number of moves that each ghost will remain
 
        scared because of Pacman having eaten a power pellet." jika lebih dari 0, maka final score akan bertambah
            final_score+=1

if len(temporaryfood)!=0: --> jika panjang dari temporaryFood tidak sama dengan 0, maka nilai yang didalam temporaryFood akan dimasukan ke variabel minimalFood dari item yang terkecil
            
            minimalFood = min(temporaryfood)
         
            if minimalFood <5 and minimalGhost >=8: --> 
                final_score+=1.5
            elif minimalFood <5 and minimalGhost<8:
                final_score-=1
            if minimalFood >=5 and minimalGhost>=8:
                final_score+=0.15
            else:      -----> jika ada keadaan yang tidak memenuhi keadaan diatas, maka final_score akan minus 1. selajutnya jika actionnya tidak "Stop", maka final_score akan ditambah 1
                final_score-=1
                if action != "Stop":
                    final_score+=1
           
        return final_score

    dalam mengerjakan problem nomer 1 saya membutuhkan waktu sekitar lebih dari 6 hari,karena saya merasa kesusahan untuk memikirkan algoritmanya dan ada beberapa algoritma yang kurang saya pahami jadi saya butuh bantuan beberapa teman untuk bersama sama menyelesaikannya

***************************************************************************************************************
    QUESTION 2 : MINIMAX

     def minimax(state, agent, depth, maximalPlayer): --> langkah pertama adalah membuat function yang memiliki paramater seperti diatas
            if state.isWin() or state.isLose(): ---> lalu saya membuat pengecekan or, yaitu jika dua duanya benar atau sekurang kurangnya salah satunya benar, maka akan direturn self.evaluationFunction(state)
                return self.evaluationFunction(state)

     if maximalPlayer is True:  --> jika maximalPlayernya bernilai True, maka  maximalEvaluation akan bernilai negatif infinity
                maximalEvaluation = float('-inf')
                value = maximalEvaluation --> negatif infinity akan dimasukan kedalam value
                behaviourBest = "Stop"
               ---->>> selanjutnya terjadi looping.
                for action in state.getLegalActions(agent):
                    childState = state.getNextState(agent, action) --> mengidentifikasi childState
                    value = minimax(state=childState, agent=1, depth=depth, maximalPlayer=False ) -->mengidentifikasi value 
                    if value > maximalEvaluation: --> lalu melakukan pengecekan. jika value > maximalEvaluation, maka behaviourBestnya akan menjadi action dan maximalEvaluationnya menjadi value.
                lalu terjadi pengecekan lagi yaitu : 
                if depth == self.depth:
                    return behaviourBest
                else:  --> jika depth tidak sama dengan self.depth maka yang direturn adalah nilai dari macimalEvaluation
                    return maximalEvaluation
    Jika maximalPlayer bernilai False, maka akan dibuat variabel nextNewAgent yang merupakan pengidentifikasian dari agent + 1.
    jika nextNewAgent == state.getNumAgents()--> maka nextNewAgent akan bernilai 0, jika nextNewAgent bernilai sama dengan 0, maka depthnya akan dikurani 1. 

     minimalEvaluation = float('inf') ---> pengidentifikasian minimalEvaluation yaitu positif infinite
                value = minimalEvaluation  --> lalu memasukannya ke dalam variabel value
                for action in state.getLegalActions(agent): --> terjadi looping untuk mengidentifikasi childState dan pengecekan nextNewAgent
                    childState = state.getNextState(agent, action) 
                    if nextNewAgent == 0: 
                        if depth == 0: jika depthnya sama dengan 0, maka  value = self.evaluationFunction(childState), jika tidak maka, valunya adalah def minimax dengan paramater maximalPlayer yang bernilai true.
                    jika nextNewAgent tidak bernilai 0, maka valuenya adalah def minimax dengan paramater maximalPlayer yang bernilai false
                    setelah nilai value sudah ditentukan, selanjutnya adalah pengecekan if yaitu mengecek apkah value kurang dari minimalEvaluation. jika iya, maka minimalEvaluation sama dengan value.
                return minimalEvaluation 



        return minimax(state=gameState, agent=0, depth=self.depth, maximalPlayer=True)


        pada q2 saya mengerjakan problemnya kurang lebih satu minggu, seperti q1 saya juga membutuhkan beberapa bantuan dan menurut saya ini lebih susah daripada q1 karena awalnya saya kesusahan untuk mengerti fungsi dari function minimax



    ******************************************************************************************************

    QUESTION 3

     def minimax(state, agent, depth, alpha, beta, maximalPlayer):
            if state.isWin() or state.isLose():
                return self.evaluationFunction(state)
            if maximalPlayer is True:
                maximalEvaluation = float('-inf')
                value = maximalEvaluation
                bestAction = "Stop" 
                for action in state.getLegalActions(agent):
                    childState = state.getNextState(agent, action)
                    value = minimax(state=childState, agent=1, depth=depth, alpha=alpha, beta=beta, maximalPlayer=False)
                    if value > maximalEvaluation:
                        bestAction = action
                        maximalEvaluation = value

                    pada bagian di atas,  algoritmanya sama dengan algoritma pada question 2. yang membedakan adalah adanya penambahan paramater alpha dan beta pada fungsi minimax. selain itu yang membdedakan juga adalah pengecekan alpha dan  beta

                    masih di dalam loopingan for, terjadi pengecekan apakah value lebih dari alpha, jika ya maka alpha sama dengan value. selanjutnya terjadi pengecekan alpha apakah lebih besar dari beta, jika ya maka break.


                if depth == self.depth:
                    return bestAction
                else:
                    return maximalEvaluation
            else:
                nextNewAgent = agent + 1
                if nextNewAgent == state.getNumAgents():
                    nextNewAgent = 0
                if nextNewAgent == 0:
                    depth -=1
                minimalEval =  float('inf')
                value = minimalEval
                for action in state.getLegalActions(agent):
                    childState = state.getNextState(agent, action)
                    if nextNewAgent == 0:
                        if depth == 0:
                            value = self.evaluationFunction(childState)
                        else:
                            value = minimax(state=childState, agent=nextNewAgent, depth=depth, alpha=alpha, beta=beta, maximalPlayer=True)
                    else:
                        value = minimax(state=childState, agent=nextNewAgent, depth=depth, alpha=alpha, beta=beta, maximalPlayer=False)
                    
                Nah algoritma di atas juga sama percis dengan algoritma pada q2, hanya saja pada pengidentifikasian value yang diidentifikasi menjadi fungsi minimax, paramater pada fungsi mmminimax di q3 meimiliki tambahan paramater yaitu sesuai dengan masalahnya adalah alpaha dan beta.

                if value <  minimalEval:
                        minimalEval = value
                    if value < beta:
                        beta = value
                    if beta < alpha:
                        break
                return minimalEval

        return minimax(state=gameState, agent=0, depth=self.depth, alpha=float('-inf'), beta=float('inf'), maximalPlayer=True)

        terakhir, yang direturn adalah fungsi minimax dimana alpha nya sama dengan positif inf dan betnya menjadi negatif inf, selain itu maximalPlayernya juga bernilai true.


        pada q3 saya menyelesaikannya di hari hari menjelang deadline dan hanya sekitar 3-4 hari. 
       



        QUESTION 4 & 5 tidak sempeat saya baca permasalahannya karna waktunya sudah mendekati deadline
