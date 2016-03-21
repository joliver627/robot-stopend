void stop_end(void) //version1.0
{
    OpenTimer0(TIMER_INT_OFF & T0_SOURCE_INT & T0_16BIT & T0_PS_1_256);
    _delay(4);
    TMR0IF = 0;
        WriteTimer0(0);
    
        while(ReadTimer0() <= 10000)
        {
    
        check_sensors();
        if((SeeLine.B) != 0b11111u)
        {
            return;
        }
        set_leds();
    }
    motors_brake_all;
}
  
  
    void stop_end(void)//version2.0
{
    OpenTimer0(TIMER_INT_OFF & T0_SOURCE_INT & T0_16BIT & T0_PS_1_256);
    _delay(4);
    TMR0IF = 0;
        WriteTimer0(0);
    
        while(ReadTimer0() <= 10000)
        {
    
        check_sensors();
        if((SeeLine.B) != 0b11111u)
        {
            return;
        }
        set_leds();
    }
    set_motor_speed(left, stop, 0); 
  set_motor_speed(right, stop, 0); 
}
