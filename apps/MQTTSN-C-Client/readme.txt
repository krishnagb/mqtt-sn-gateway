This package provides a reference implementation of the client side of the MQTT-SN (MQTT for Sensor Networks) 
protocol.

The reference implementation consists of the following files: 
                        disconnect, register, publish, etc. for communicating with the gateway/broker. 
                        The use of these verbs is explained below. It also defines the various parameters 
                        values required for the operation of the MQTT-SN protocol.
                        the client. It contains the client handling of the MQTT-SN protocol. 
                        and a generic platform. To port the reference implementation to a specific hardware platform, 
                        the functions defined in this header file have to be implemented.

implemented by the platform (see also file gp_api.h):
to be called back when the timer times out is given as parameter. If the timer could be created, 
the platform assigns to it a one-byte identity and returns that identity to the MQTT-SN client. The client 
will use this identity later on to start, stop, and end the timer. If the timer could not be created, 
the value 0xFF should returned.
timer that should be started (this id was returned to the client when the timer was created). The two-byte long 
time-out value (in seconds) is indicated by msb and lsb, with msb containing the most significant byte and lsb 
the least significant byte of the value.
is indicated by the parameter id.
timer to be freed is indicated by the parameter id. 
the first byte of the array which contains the MQTT-SN message to be sent. The length of the message is indicated 
by this first byte. The array containing the destination address is pointed by *dest and its length is indicated 
by the parameter length.
to the first byte of the array containing the MQTT-SN message to be broadcasted. The length of the MQTT-SN 
message is indicated by this first byte. The parameter radius indicates the broadcast radius.
message received is indicated by the pointer *msg; this first byte also contains the length of the message. 
The address of the sender is indicated by the pointer *sender, and its length by the parameter length. 
The platform can release the buffer containing the message when this function returns.
and indicated to it by the callback function gpcb_network_msg_received(…). The pointer *msg is the one 
in the callback function, and the parameter index is the index of the byte to get. Note that the first 
byte of the MQTT-SN message has the index 1! Note also that the client will call this function only 
while it processes the callback function gpcb_network_msg_received(…).
