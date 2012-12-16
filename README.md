struct ddatum{
       int dan,mj,god;
       };

struct element {
       char prez_ime[40];
       ddatum dat;
       float tekuci,devizni;
       int a,b,c,d;
       };

struct qu2 {
       element korisnik;
       qu2 *sljedeci;
       };

struct qu1 {
       qu2 *front,*rear;
       }; 
       
qu1 q,salter,brzi,novi;
int n,platiti=0;
typedef qu1& red;

element frontq(qu1& q) {
     if(q.front==q.rear) exit(0);
     return (q.front->sljedeci)->korisnik;
     }
     
void enqueueq(element x,qu1& q) {
     qu2 *zadnji = q.front,*novi;
     while(zadnji->sljedeci) zadnji=zadnji->sljedeci;
     novi = new qu2;
     novi->sljedeci=NULL;
     novi->korisnik=x;
     zadnji->sljedeci=novi;
     q.rear=novi;
     }
     
void dequeueq(qu1& q) {
     if(q.front==q.rear) return;
     qu2 *brisi = q.front;
     q.front=brisi->sljedeci;
     delete brisi;
     }

bool isemptyq(qu1& q) {
     if(q.front==q.rear) return true;
     else return false;
     }
     
void initq(qu1& q) {
     qu2* novi = new qu2;
     novi->sljedeci=NULL;
     q.rear=novi;
     q.front=novi;
     } 
