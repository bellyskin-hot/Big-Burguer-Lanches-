# Big-Burguer-Lanches-
Lanchonete e hamburgueria
// Arquivo principal do site Big Burguer

import { useState } from "react"; import { Button } from "@/components/ui/button";

const lanches = [ { id: 1, nome: "Xixia", preco: 18.99, estoque: 10 }, { id: 2, nome: "Ben", preco: 16.99, estoque: 8 }, { id: 3, nome: "Pititinha", preco: 14.99, estoque: 5 }, { id: 4, nome: "Dindinha", preco: 20.99, estoque: 7 }, { id: 5, nome: "Nanan", preco: 19.99, estoque: 6 }, { id: 6, nome: "Maricota", preco: 22.99, estoque: 4 }, ];

export default function Home() { const [carrinho, setCarrinho] = useState([]);

const adicionarAoCarrinho = (lanche) => { if (lanche.estoque <= 0) return;

setCarrinho([...carrinho, lanche]);
lanche.estoque -= 1;

};

const mensagemWhatsApp = carrinho.map(item => 🍔 ${item.nome} - R$ ${item.preco.toFixed(2)}).join("%0A");

const linkWhatsApp = https://wa.me/5586998770591?text=Olá! Quero fazer o seguinte pedido:%0A${mensagemWhatsApp};

return ( <div className="p-4 bg-black text-orange-400 min-h-screen"> <h1 className="text-4xl font-bold mb-6">Big Burguer 🍔</h1> <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-4"> {lanches.map((lanche) => ( <div key={lanche.id} className="border border-orange-500 rounded-2xl p-4 shadow-lg"> <h2 className="text-2xl font-semibold">{lanche.nome}</h2> <p className="text-lg">R$ {lanche.preco.toFixed(2)}</p> <p className="text-sm">Estoque: {lanche.estoque}</p> <Button onClick={() => adicionarAoCarrinho(lanche)} className="mt-2 bg-orange-500 text-white hover:bg-orange-600"> Adicionar ao carrinho </Button> </div> ))} </div>

{carrinho.length > 0 && (
    <div className="fixed bottom-4 right-4 bg-orange-600 text-white p-4 rounded-xl shadow-xl">
      <p>{carrinho.length} item(ns) no carrinho</p>
      <a href={linkWhatsApp} target="_blank">
        <Button className="mt-2 bg-black hover:bg-gray-900">
          Finalizar pedido no WhatsApp
        </Button>
      </a>
    </div>
  )}
</div>

); }

