---
layout: post
title: "Comment rater un entretien d'embauche"
date: 2017-01-25 17:36:35 +0100
comments: true
published: true
categories: [Une pensee]
author: jeremy
---

Le pair-programming, quelle merveilleuse invention ... Enfin bref ...

Il y a un moment, j'avais fait un article sur "Comment réussir son entretien d'embauche en 9 points".

Je me devais donc de faire cette fois-ci un article sur "Comment rater un entretien d'embauche" mais pas en 9 points cette fois-ci, c'est beaucoup plus simple de rater que de réussir ...

# *Etape 1 : Faîtes du pair-programming*
Retenez bien une chose, c'est toujours plus dur de passer à l'oral devant une assemblée que tout seul. Et puis, un ordinateur c'est UN clavier et UNE souris non ?!
<!--break-->
# *Etape 2 : Ne parlez pas !*
...

# *Etape 3 : Ne faîtes pas de tests dans votre code Ruby*
Oui, je connais RSPEC, minitest, testunit mais non, je ne les utilise pas, ni quotidiennement, ni annuellement. Mais promis je vais commencer à m'y intérresser ...

# *Etape 4 : Soyez honnêtes !*
Écoutez, je vais être honnête mais **je ne sais pas** ...

# *Etape 5 : N'apprenez pas ce boût de code PAR COEUR !*

```ruby
require 'test/unit'
class AssertionError < RuntimeError; end;

class Assertion
  attr_accessor :arg
  def initialize(arg)
    @arg = arg

  end
  def to(expectation)
    raise AssertionError if !expectation
  end

  def not_to(expectation)
    raise AssertionError if expectation
  end
end



class TestCase < Test::Unit::TestCase
  def expect(arg)
    @assert = Assertion.new(arg)
  end

  def eq(arg)
    if @assert.arg == arg
      return true
    else
      return false
    end
  end

  def be_greater_than(arg)
    if @assert.arg > arg
      return true
    else
      return false
    end
  end
end




class Rspec < TestCase
  def test_should_be_ok
    assert_nothing_raised(AssertionError) { expect(6).to eq(6)}
  end

  def test_should_not_be_ok
    assert_raise(AssertionError){ expect(6).not_to eq(6)}
  end

  def test_should_raise_error
    assert_raise(AssertionError){ expect(6).to eq(4)}
  end

  def test_should_not_raise_error
    assert_nothing_raised(AssertionError) { expect(6).not_to eq(4)}
  end

  def test_should_error
    assert_raise(AssertionError){ expect(6).not_to be_greater_than(4)}
  end

  def test_should_not_error
    assert_nothing_raised(AssertionError){ expect(4).not_to be_greater_than(6)}
  end

  def test_not_error
    assert_nothing_raised(AssertionError){ expect(6).to be_greater_than(4)}
  end

  def test_error
    assert_raise(AssertionError){ expect(4).to be_greater_than(6)}
  end
end

```
# *Bonus : Quesqu'un DSL*
 Un DSL est un langage propre à un métier ou à une société qui suit un formalisme défini et compact. On peut ensuite faire le pont entre ce langage simple assimilable par tous sans prérequis informatique et un langage de programmation générique, tel que du C ou du Java.
