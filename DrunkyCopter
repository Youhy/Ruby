#Evgeny Pozdnyakov
require 'curses'
include Curses

init_screen
curs_set(frame = 0)
hight=10

while (frame += 1)
  clear
  [
      %|      0123443210-*-0123443210  |,
      %|                 I             |,
      %|012       ~~~~~~@@@~~~         |,
      %|3O3======{        [ ] ))       |,
      %|210       \\            ))     |,
      %|           \\____________)))   |,
      %|              Y     Y          |,
      %|          ------   ------      |,
  ].each_with_index do |line, id|
    { 0 => [':ROAR', 5], (2..4) => ['\    ', 4]}.each do |key, (ch, n)|
      n.times { |i| line.tr!(i.to_s, ch.chars.to_a[(i + frame) % n]) } if key === id
    end

    drunkycopter = (line + (' ' * (cols - 31))).chars.to_a
    frame.times { drunkycopter.unshift(drunkycopter.pop) }

    setpos(hight + id, 0)
    addstr drunkycopter.join
  end

  case rand 1..10
    when 1
      hight -= 1
    when 10
      hight += 1
  end

  refresh
  sleep 0.08
end

at_exit { close_screen }
