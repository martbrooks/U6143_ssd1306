Target		= pirack_oled_display
CXX         	= gcc
ODIR		= obj
SRC		=$(wildcard *.c)
DIR		=$(notdir $(SRC))
OBJ 		= $(patsubst %.c, %.o, $(DIR))
$(Target): $(OBJ)
	$(CXX) $^ -o $@ -g -rdynamic 
.PHONY:clean
clean:
	rm -rf *.o
	rm -rf $(Target)

install:
	install -o root -g root -m 0755 -d /usr/local/bin
	install -o root -g root -m 0755 pirack_oled_display /usr/local/bin
	install -o root -g root -m 0655 pirack_oled_display.service /etc/systemd/system/pirack_oled_display.service
	systemctl daemon-reload
	systemctl enable pirack_oled_display.service
	systemctl start pirack_oled_display.service
