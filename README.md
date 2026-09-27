#!/usr/bin/env ruby
# frozen_string_literal: true

class SecurityResearcher
  def initialize
    @consciencia = :limpa
  end

  def achar_exploits
    exploits = sistema.scan(/bugs/)
    puts "Encontrei #{exploits.size} coisas que não deveriam estar ali."
    exploits
  end

  def reportar(exploits)
    exploits.each { |e| disclosure.responsavel(e) }
    @consciencia = :tranquila
  end

  def dormir
    sleep(8.hours)
  rescue Insomnia
    retry
  ensure
    puts "Durmo bem. Às vezes."
  end

  def ciclo_de_vida
    loop do
      achar_exploits
      reportar
      dormir
    end
  end
end

SecurityResearcher.new.ciclo_de_vida
