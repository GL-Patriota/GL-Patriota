import React, { useState } from "react";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import Image from "next/image";
import Head from "next/head";

const WHATSAPP_NUMBER = "5599999999999";
const WHATSAPP_MSG = "Olá, quero saber mais sobre a figura de ação Gabriel Lima!";
const WHATSAPP_LINK = `https://wa.me/${WHATSAPP_NUMBER}?text=${encodeURIComponent(WHATSAPP_MSG)}`;

function Header() {
  return (
    <header className="text-center py-10 shadow-md">
      <h1 className="text-4xl font-bold tracking-wide">GL Patriota</h1>
      <p className="mt-2 text-xl italic">Por Deus, pela Pátria e pelo Futuro</p>
    </header>
  );
}

function HeroSection() {
  return (
    <section className="text-center py-12 px-4">
      <Image
        src="/figura-acao.png"
        alt="Figura de ação colecionável de Gabriel Lima com terno azul e acessórios patrióticos"
        width={256}
        height={256}
        className="mx-auto shadow-xl rounded-2xl"
      />
      <h2 className="text-3xl font-bold mt-6">A Figura do Patriota</h2>
      <p className="mt-4 max-w-xl mx-auto text-lg">
        Uma representação de coragem, fé e amor pelo Brasil. Adquira agora a figura de ação colecionável de Gabriel Lima e apoie essa causa.
      </p>
      <div className="flex justify-center gap-4 mt-6">
        <Button className="bg-green-600 hover:bg-green-700">Comprar Agora</Button>
        <a href={WHATSAPP_LINK} target="_blank" rel="noopener noreferrer">
          <Button variant="outline">Falar no WhatsApp</Button>
        </a>
      </div>
    </section>
  );
}

function Sobre() {
  return (
    <section className="bg-blue-900 py-12 px-6 text-center">
      <h3 className="text-2xl font-bold mb-4">Quem é Gabriel Lima?</h3>
      <p className="max-w-2xl mx-auto text-lg">
        Gaúcho, defensor da juventude e do futuro do Brasil. Candidato a deputado federal em 2026, Gabriel representa a fé, a honra e a força do povo brasileiro.
      </p>
    </section>
  );
}

function Checkout() {
  const [loading, setLoading] = useState(false);

  const handleCheckout = () => {
    setLoading(true);
    setTimeout(() => {
      alert("Pagamento simulado com sucesso! Obrigado por apoiar a causa!");
      setLoading(false);
    }, 2000);
  };

  return (
    <div className="flex justify-center gap-4 mt-4">
      <Button onClick={handleCheckout} disabled={loading} className="bg-green-600 hover:bg-green-700">
        {loading ? "Processando..." : "Finalizar Compra"}
      </Button>
      <a href={WHATSAPP_LINK} target="_blank" rel="noopener noreferrer">
        <Button variant="outline">WhatsApp</Button>
      </a>
    </div>
  );
}

function Loja() {
  return (
    <section className="py-12 px-6 text-center">
      <h3 className="text-2xl font-bold mb-6">Loja</h3>
      <Card className="max-w-md mx-auto">
        <CardContent className="p-6">
          <Image
            src="/figura-acao.png"
            alt="Figura de ação colecionável de Gabriel Lima com terno azul e acessórios patrióticos"
            width={400}
            height={400}
            className="w-full rounded-xl"
          />
          <h4 className="text-xl font-bold mt-4">Figura de Ação Gabriel Lima</h4>
          <p className="mt-2 text-sm text-gray-300">
            Inclui: mochila camuflada, Bíblia, bandeira do Brasil, caneta BIC, laptop e boné "Vamos fazer o Brasil grande".
          </p>
          <p className="mt-2 text-lg font-bold">R$ 97,00</p>
          <Checkout />
        </CardContent>
      </Card>
    </section>
  );
}

function Contato() {
  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    alert("Mensagem enviada com sucesso!");
  };

  return (
    <section className="bg-blue-900 py-12 px-6">
      <h3 className="text-2xl font-bold text-center mb-6">Contato</h3>
      <form onSubmit={handleSubmit} className="max-w-xl mx-auto space-y-4">
        <Input placeholder="Seu nome" required />
        <Input placeholder="Seu e-mail" type="email" required />
        <Textarea placeholder="Sua mensagem" required />
        <Button type="submit" className="bg-green-600 hover:bg-green-700 w-full">Enviar</Button>
      </form>
    </section>
  );
}

function Footer() {
  return (
    <footer className="text-center py-6 bg-blue-950 border-t border-blue-800 text-sm">
      © 2025 GL Patriota. Todos os direitos reservados.
    </footer>
  );
}

export default function Home() {
  return (
    <div className="bg-blue-950 text-white min-h-screen font-sans">
      <Head>
        <title>GL Patriota - Gabriel Lima</title>
        <meta name="description" content="Adquira a figura de ação Gabriel Lima e apoie a mudança do Brasil." />
      </Head>
      <Header />
      <HeroSection />
      <Sobre />
      <Loja />
      <Contato />
      <Footer />
    </div>
  );
}
