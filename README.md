# COUNTINGSORT

public void CountingSort(Integer[] array, int leftIndex, int rightIndex) {
		
		//Encontrar o maior valor 
		int k = 0;
		for(int m = leftIndex; m < rightIndex; m++){
			if(array[m] > k){
				k = array[m];
			}
		}
		
		//Cria vetor com o tamanho do maior elemento
		int[] vetorTemporario = new int[k];
		
		//Inicializar com zero o vetor temporario
		for(int i = 0; i < vetorTemporario.length; i++){
			vetorTemporario[i] = 0;
		}
		
		//Contagem das ocorrencias no vetor desordenado
		for(int j = leftIndex; j < rightIndex; j++){
			vetorTemporario[array[j]] += 1;
		}
		
		//Fazendo o  complemento do numero anterior 
		for(int i = leftIndex; i < k; i++){
			vetorTemporario[i] = vetorTemporario[i] + vetorTemporario[i - 1];
		}
		
		//Ordenando o array da direita para a esquerda
		int[] vetorAuxiliar = new int[array.length];
		for(int j = rightIndex; j > leftIndex; j--) {
			vetorAuxiliar[vetorTemporario[array[j]]] = array[j];
			vetorTemporario[array[j]] -= 1; 
		}
		
		//Retornando os valores ordenados para o vetor de entrada
		for (int i = leftIndex; i < rightIndex; i++){
			array[i] = vetorAuxiliar[i];
		}
	}
