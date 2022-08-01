fun main() {
    //ARRAYS
    val vetorInt = IntArray(5)
    val vetorInt2 = intArrayOf(1, 2, 3, 5, 8)

    val vetorStr = Array(5) {""}
    val vetorStr2 = arrayOf("Maria", "Ze", "Umberto")
    
    val vetorDouble = DoubleArray(5)
    val vetorDouble2 = doubleArrayOf(500.0, 2000.0, 5000.0)
    

                    //Atribuição individual
                   vetorInt[0] = 8
                   vetorInt[1] = 5
                   vetorInt[2] = 2
                   vetorInt[3] = 2
                   vetorInt[4] = 7

    //PRINTS ARRAYS
    println("==========for==========")
    for(valor in vetorInt2) {
        println(valor)
    }
    println("==========forEach==========")
    vetorInt.forEach {
        println(it)
    }
    println("==========forEach + sort==========")
    vetorInt.sort()
    vetorInt.forEach { elemento ->
                       println(elemento)
                     }
    println("==============================")
    //OPERAÇÕES ARRAYS
    println("Maior valor do vetor: " + vetorInt.maxOrNull())
    println("Menor valor do vetor: " + vetorInt.minOrNull())
    println("Media dos valores do vetor: " + vetorInt.average())
    println("Filtrar maiores que 5 -> " + vetorInt.filter{ it > 5})
    println("Quantidade de numeros de 1 a 4: " + vetorInt.count{it in 1..4})
    println("Procurar numero 3: " + vetorInt.find{it == 3}) // return Int ou Null
    println("Ha algum numero 7? " + vetorInt.any{it == 7}) // return Boolean
    println("\n ==============COLLECTIONS===============")
    
    
    
    //LISTAS
    val joao = Funcionario("Joao", 5200.0, "CLT")
    val maria = Funcionario("Maria", 3400.0, "PJ")
    val zeke = Funcionario("Zeke", 1212.0, "CLT")
    val SALARIO_MINIMO:Double = 1212.0
    println("\n ----------listOf----------")   
    val funcionarios = listOf(joao, maria, zeke)
    
    funcionarios.forEach{println(it)}
    
    println("Quem recebe o salario minimo? \n" + funcionarios.find{it.salario == SALARIO_MINIMO})
    funcionarios
        .sortedBy{it.salario} //crescente
        .forEach{println(it)}
     println("\n --------------------")   
    funcionarios
        .groupBy{it.tipo}
        .forEach{print{it}}
    
    println("\n ----------setOf----------")   
    val funcionarios1 = setOf(joao, zeke)
    val funcionarios2 = setOf(maria)
    
    val resultUnion = funcionarios1.union(funcionarios2)
    println("Union: \n " + resultUnion)
    
    val resultSubtract = resultUnion.subtract(funcionarios2)
    println("Subtract (joao, zeke, maria) - (maria): \n" + resultSubtract)
    
    val resultIntersect = resultUnion.intersect(funcionarios2)
    println("Intersect: (joao, zeke, maria) e (maria): \n" + resultIntersect)
    
    
    println("\n ----------mapOf----------")   
    val pair: Pair<String, Double> = Pair("Joao", 4500.0) //init 1
    val dic1 = mapOf(pair)
    val dic2 = mapOf(
        "Joao" to 5400.0,
        "Jorge" to 2500.0,
        "Jericho" to 1212.0
        ) //init 2
    dic2.forEach{
        (k, v) -> println("Chave: $k - Valor: $v")
    }
       println("\n ==============COLLECTIONS MUTABLE===============")
	println("\n ----------mutableLisOf----------")
	val muList = mutableListOf(joao, maria)
	muList.forEach{println(it)}
	muList.add(zeke) 
	println("Add Zeke \n")
	muList.forEach{println(it)}
	println("Remove Maria \n")
	muList.remove(maria)
	muList.forEach{println(it)}
	
	println("\n ----------mutableSetOf----------")
	val muSet1 = mutableSetOf(joao, maria)
	val muSet2 = mutableSetOf(zeke)
	println(muSet1.intersect(muSet2))
	println("Sem elemento comum: ")
	println(muSet1.intersect(muSet2) == mutableSetOf(maria))
	muSet2.add(maria)
	println("Com elemento comum: ")
	println(muSet1.intersect(muSet2) == mutableSetOf(maria))
	println(muSet1.intersect(muSet2))
	
	println("\n ----------mutableMapOf----------")       
    val muMap = mutableMapOf(
        "joao" to 2500.00,
        "maria" to 3000.00,
        "jeff" to 1212)
    println(muMap)
       
}

data class Funcionario(
    val nome: String,
    val salario: Double,
    val tipo: String,
) {
override fun toString(): String =
"""
    Nome:       $nome
    Salario:    $salario
""".trimIndent()
}
