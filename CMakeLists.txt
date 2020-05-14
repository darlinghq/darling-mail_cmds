project(mail_cmds)

set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -nostdinc")

add_darling_executable(mail
	mail/aux.c
	mail/cmdtab.c
	mail/cmd1.c
	mail/cmd2.c
	mail/cmd3.c
	mail/collect.c
	mail/edit.c
	mail/fio.c
	mail/getname.c
	mail/head.c
	mail/lex.c
	mail/list.c
	mail/main.c
	mail/names.c
	mail/popen.c
	mail/quit.c
	mail/send.c
	mail/strings.c
	mail/temp.c
	mail/tty.c
	mail/vars.c
	mail/version.c
	mail/v7.local.c
)

add_darling_executable(biff biff/biff.c)

add_darling_executable(comsat comsat/comsat.c)

add_darling_executable(msgs msgs/msgs.c)
target_link_libraries(msgs system ncurses)

install(TARGETS mail biff comsat msgs DESTINATION libexec/darling/usr/bin)
install(FILES
	biff/biff.1
	from/from.1
	mail/mail.1
	mail/mailx.1
	msgs/msgs.1
	DESTINATION libexec/darling/usr/share/man/man1)
install(FILES comsat/comsat.8 DESTINATION libexec/darling/usr/share/man/man8)

# Hardlink on macOS
InstallSymlink(mail "${CMAKE_INSTALL_PREFIX}/libexec/darling/usr/bin/mailx")

