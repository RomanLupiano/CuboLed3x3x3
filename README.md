# CuboLed3x3x3
El proyecto consta de realizar un cubo de 3 leds de ancho, 3 de largo y 3 de altura, donde se pueden realizar patrones con cada led independiente.

Requerimientos:  
- Arduino Uno  
- 27 leds  
- 27 cables  
- 9 resistencias de 150ohm  
- 3 resistencias de 10 kohm  
- 3 transistores 2N2222A  
- 2 protoboard  

Sketch de la estructura: https://www.tinkercad.com/things/00kEsJWfYTc-funky-kup/editel?sharecode=uhpk7Fg1wopNbBx8SOBcNdQvvM27X9o572D43Cfaffo
___

## El código
1. El objeto Cubo
2. Sus funciones
3. Ejemplo

### El objeto Cubo
    class LedCube
    {
    public:
    LedCube(byte size, byte levelPins[], byte colPins[]);
    ~LedCube();
    
    byte getCols(){ return cols; }
    byte getLevels(){ return levels; }
    byte getNumLights(){ return num; }
    
    void light(byte level, byte col, byte val);
    void lightOn(byte level, byte col);
    void lightOff(byte level, byte col);
    void lightPulse(byte level, byte col, unsigned int wait = 5);
    void lightSequence(byte seq[], byte length, unsigned int time = 5, byte gap = 1);
    void lightLevel(byte r, unsigned int wait = 50);
    void lightRow(byte r, byte level, unsigned int wait = 50);
    void lightPlane(byte r, unsigned int wait = 50);
    void lightColumn(byte col, unsigned int wait = 50);
    void lightDrop(byte col, unsigned int wait = 50);
    void lightPerimeter(byte level, byte rotations, unsigned int wait = 50);
    void randomLight(byte numLights, unsigned int wait = 50);
    void randomColumn(byte numColumns = 1, unsigned int wait =  50);
    void lightsOut(unsigned int wait =  5);
    
    cubeFrame* createFrame(byte sequence[], unsigned int length, unsigned int delay);
    void destroyFrame(cubeFrame* frame);
    void lightFrames(cubeFrame* frames[], unsigned int length);
    
    void enableBuffer(boolean enable = true);
    void invertBuffer(boolean invert = true);
    void clearBuffer();
    void fillBuffer();
    void drawBuffer(unsigned int wait = 1);
    byte getBufferAt(byte lv, byte col);
    
    private:
    byte levels;
    byte cols;
    byte num;
    byte **buffer;
    byte *colPins;
    byte *levelPins;
    boolean bufferEnabled;
    boolean bufferInverted;
    
    void setBuffer (byte val);
    };
