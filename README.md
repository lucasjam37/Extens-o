# Extens-o
App android em React Native
import React, { useState } from 'react';
import { View, TextInput, StyleSheet, Button } from 'react-native';

export default function CadastroProdutos() {
  const [nomeProduto, setNomeProduto] = useState('');
  const [precoProduto, setPrecoProduto] = useState('');
  const [quantidadeProduto, setQuantidadeProduto] = useState('');

  const cadastrarProduto = () => {
    // Salva as informações do produto em um banco de dados ou arquivo local
    // Ex: firebase.firestore().collection('produtos').add({nome: nomeProduto, preco: precoProduto, quantidade: quantidadeProduto});
  }

  return (
    <View style={styles.container}>
      <TextInput
        style={styles.input}
        onChangeText={setNomeProduto}
        value={nomeProduto}
        placeholder="Nome do produto"
      />
      <TextInput
        style={styles.input}
        onChangeText={setPrecoProduto}
        value={precoProduto}
        placeholder="Preço do produto"
      />
      <TextInput
        style={styles.input}
        onChangeText={setQuantidadeProduto}
        value={quantidadeProduto}
        placeholder="Quantidade disponível no estoque"
      />
      <Button
        title="Cadastrar"
        onPress={cadastrarProduto}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: 'center',
    justifyContent: 'center',
  },
  input: {
    height: 40,
    width: '80%',
    margin: 12,
    borderWidth: 1,
    padding: 10,
  },
});

import React, { useState } from 'react';
import { View, Text, TextInput, StyleSheet, Button } from 'react-native';

export default function ControleDeVendas() {
  const [cliente, setCliente] = useState('');
  const [produtos, setProdutos] = useState([]);
  const [valorTotal, setValorTotal] = useState('');

  const adicionarProduto = (produto) => {
    setProdutos([...produtos, produto]); // Adiciona o produto selecionado à lista de produtos vendidos
  }

  const removerProduto = (produto) => {
    const novosProdutos = produtos.filter((p) => p !== produto); // Remove o produto selecionado da lista de produtos vendidos
    setProdutos(novosProdutos);
  }

  const calcularValorTotal = () => {
    let total = 0;
    for (const produto of produtos) {
      total += produto.preco;
    }
    setValorTotal(total); // Calcula o valor total da venda com base nos produtos selecionados
  }

  const finalizarVenda = () => {
    // Registra a venda no banco de dados ou arquivo local
    // Ex: firebase.firestore().collection('vendas').add({cliente: cliente, produtos: produtos, valorTotal: valorTotal});
    setCliente('');
    setProdutos([]);
    setValorTotal('');
  }

  return (
    <View style={styles.container}>
      <TextInput
        style={styles.input}
        onChangeText={setCliente}
        value={cliente}
        placeholder="Nome do cliente"
      />
      <Button
        title="Adicionar produto"
        onPress={() => adicionarProduto({nome: 'Pão francês', preco: 0.50})}
      />
      {produtos.map((produto, index) => (
        <View key={index}>
          <Text style={styles.produto}>{produto.nome} - R$ {produto.preco}</Text>
          <Button
            title="Remover"
            onPress={() => removerProduto(produto)}
          />
        </View>
      ))}
      <Text style={styles.valorTotal}>Valor total: R$ {valorTotal}</Text>
      <Button
        title="Finalizar venda"
        onPress={finalizarVenda}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: 'center',
    justifyContent: 'center',
  },
  input: {
    height: 40,
    width: '80%',
    margin: 12,
    borderWidth: 1,
    padding: 10,
  },
  produto: {
    fontSize: 16,
    margin: 5,
  },
  valorTotal: {
    fontSize: 20,
    fontWeight: 'bold',
    margin: 15,
  },
});
import React, { useState } from 'react';
import { View, Text, TextInput, StyleSheet, Button } from 'react-native';

export default function ControleDeEstoque() {
  const [nomeProduto, setNomeProduto] = useState('');
  const [precoProduto, setPrecoProduto] = useState('');
  const [quantidadeDisponivel, setQuantidadeDisponivel] = useState('');

  const cadastrarProduto = () => {
    // Salva as informações do produto em um banco de dados ou arquivo local
    // Ex: firebase.firestore().collection('produtos').add({nome: nomeProduto, preco: precoProduto, quantidade: quantidadeDisponivel});
    setNomeProduto('');
    setPrecoProduto('');
    setQuantidadeDisponivel('');
  }

  const reporEstoque = () => {
    // Atualiza a quantidade disponível do produto no banco de dados ou arquivo local
    // Ex: firebase.firestore().collection('produtos').doc('ID_do_produto').update({quantidade: novaQuantidade});
    setQuantidadeDisponivel('');
  }

  return (
    <View style={styles.container}>
      <TextInput
        style={styles.input}
        onChangeText={setNomeProduto}
        value={nomeProduto}
        placeholder="Nome do produto"
      />
      <TextInput
        style={styles.input}
        onChangeText={setPrecoProduto}
        value={precoProduto}
        placeholder="Preço do produto"
      />
      <TextInput
        style={styles.input}
        onChangeText={setQuantidadeDisponivel}
        value={quantidadeDisponivel}
        placeholder="Quantidade disponível no estoque"
      />
      <Button
        title="Cadastrar produto"
        onPress={cadastrarProduto}
      />
      <TextInput
        style={styles.input}
        onChangeText={setQuantidadeDisponivel}
        value={quantidadeDisponivel}
        placeholder="Quantidade a ser reposta no estoque"
      />
      <Button
        title="Repor estoque"
        onPress={reporEstoque}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    alignItems: 'center',
    justifyContent: 'center',
  },
  input: {
    height: 40,
    width: '80%',
    margin: 12,
    borderWidth: 1,
    padding: 10,
  },
});

import React, { useEffect, useState } from 'react';
import { View, Text, StyleSheet


  
