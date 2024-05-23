

    private static void mostrarDetalhesEmpregados(ArrayList<Empregado> empregados) {
        System.out.println("Detalhes dos Empregados:");
        for (int i = 0; i < empregados.size(); i++) {
            System.out.println("Empregado " + (i+1) + ": " + empregados.get(i));
        }
    }
}
