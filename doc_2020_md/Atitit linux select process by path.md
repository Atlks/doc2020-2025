Atitit linux select process by path


*/70 * * * * ps -ef | grep java | grep -v grep | awk '{print $2}' | xargs kill -9


