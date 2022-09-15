class ValidaCPF {
  constructor(cpfEnviado) {
      Object.defineProperty(this, 'cpfLimpo', {
          writable: false,
          enumerable: true,
          configurable: false,
          value: cpfEnviado.replace(/\D+/g, '' )
      })
  }

  SequenciaIsTrue() {
      return this.cpfLimpo.charAt(0).repeat(11) === this.cpfLimpo
  }

  geraNovoCpf() {
      const  cpfSemDigitos = this.cpfLimpo.slice(0, -2)
      const digito1 = ValidaCPF.geraDigito(cpfSemDigitos)
      const digito2 = ValidaCPF.geraDigito(cpfSemDigitos + digito1)
      this.novoCPF = cpfSemDigitos + digito1 + digito2
  }

  static geraDigito(cpfSemDigitos) {
      let total = 0
      let reverso = cpfSemDigitos.length + 1

      for(let stringNumerica of cpfSemDigitos) {
          total += reverso * Number(stringNumerica)
          reverso--
      }

      const digito = 11 - (total % 11)
      return digito <= 9 ? String(digito) : '0'
      console.log(total)
  }

  valida() {
      if(!this.cpfLimpo) return false
      if(typeof this.cpfLimpo !== 'string') return false
      if(this.cpfLimpo.length !== 11) return false
      if(this.SequenciaIsTrue()) return false
      this.geraNovoCpf()

      return this.novoCPF === this.cpfLimpo
  }
}

class GeraCPF {
  rand(min= 100000000, max= 999999999) {
    return Math.floor(Math.random()) * (max - min) + min
  }

  geraNovoCpf() {
    const cpfSemDigitos = this.rand()
    const digito1 = ValidaCPF.geraDigito(cpfSemDigitos)
    const digito2 = ValidaCPF.geraDigito(cpfSemDigitos + digito1)
    const novoCpf = cpfSemDigitos + digito1 + digito2
    return novoCpf
  }
}

(function() {
  const gera = new GeraCPF()
  const cpfGerado = document.querySelector('.cpf-gerado')
  cpfGerado.innerHTML = gera.geraNovoCpf()
})()
