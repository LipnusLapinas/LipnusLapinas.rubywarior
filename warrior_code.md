class Player
  def play_turn(warrior)
    if warrior.feel.captive?(:backward)
      warrior.rescue(:backward)!
    elsif !warrior.feel.empty?(backward)
      warrior.attack(:backward)!
    elsif warrior.feel.captive?
      warrior.rescue!
    elsif !warrior.feel.empty?
      warrior.arrack!
    elsif warrior.health != 20 && warrior.health >= @health
        warrior.rest!
    elsif !(warrior.feel(:backward).wall || @backwall == true)
      warrior.walk(:backward)!
    else
      @backwall = true
      warrior.walk!
    end
    @backwall ||= false
    @health = warrior.health
  end
end
  
