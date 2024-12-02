#include <iostream>
#include <vector>
using namespace std;

/* 

big o notacia
je to možnosť komparacia dvoch setov kodu

pokial je teda code one totožny ako code 2 ako ich budeme vzajomne porovnavať voči sebe

code 1 might be more readable than the code 2

big o je teda matematicke porovnanie / about how effcient they run

pokial mame stopky, stopne trvanie u kodu 1 trva napriklad 15 sekund nasledne u druheho kodu takne celu minutu
= volame to time complexity of the code
! vtipne je ze nie je merane v čase, pokial zoberieme rovnaky code a runneme ho na pc, ktory je dvakrat taky rychly



! --------- 1. big o worst case, best and the avarage

? omega = is the best case
? tieta = is the avarage case
? armakran pozname ho ako O = and the last one the big o is the worst case


pre priklad tu mame array o 7 prvkov
? sledujeme počet iteraci

naš best case bude sledovať čislo 1
naš najhorši case bude sledovať čislo 7
a naš avarage case bude sledovať čislo 4


! priprav sa na to ze to budeš počuvať
? bacha na to ked niekto povie avarage, worst and best case big o to sa nedeje

? but technically big o je vzdy ten najhorši case

!------ 2. big O : o(n)

lets take a look for our big o


? ako opisujeme v našej funkcii printItems(int n) pokial by n = 10 tak outputne 0 - 9

! hovorime ze tato funkcia je teda o of the n

! in the other words we are going to pass the n / and this run for the n times

? ako to vyzera grafovo

xova suradnica je n ( input ) / naopak ylonova je number of the operations
! O(n) bude vzdy straight line ( proporsional )

! drop constant pravidlo

? mame novu funkciu s našimi dvomi for loopmi

! general rule for more than function
? this function runs for the n + n times duo to reason that there are two additional for loops
? takže by sme to pisali ako O(2n) = pretoze teda n + n = 2n
! ale to nebudeme vzdy "dropneme const" aby sme dostali O(n)

? prečo to robime je aby sme prišli na broad category, do ktorej grow rate pada
! napriklad aj u 100n to rastie linearne , a to je velmi rozdielne než niečo čo rastie exponencionalne


! zapamätať takze naše prve pravidlo zjednodušovania je drop constants


!------  3. mame o of ( na na druhu )

/*

  for (size_t i{0}; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            cout << i << j << endl;
        }
    }
*/

// ! so this run n * n times / duo to reason that we are having the nested for loops
// ? vysledkom je teda n na druhu

// o of n na druhu na grafe

// ! rastie omnoho rychlejšie než o of n
// ? je to teda menej efektivne nez o of ( n )
// pokial teda dostaneme na vyber tak omnoho väčši better pick je o of n
// ? teda hovorime tu o zdvojenom for loope

// 4. pravidlo drop non-dominants
// ? jedna sa teda o dalšiu možnosť ako zjednodušujeme big o notaciu

/*

? mame tu teda nested for loop and the forloop
? o vyśledku napišeme = o(n2 + n )
! so we are asking what is the dominant term = n2
and the n will be the non-dominant term = n

? pokial by sme i nepoužiili prilišne velke čislo napr n = 100 tak by bolo n i tak less nakolko n na druhu by bolo 10000 n by sa stalo zanedbatelnym
!! takze to zjednodušujeme dropnutim n a ponechanim len n2
=== toto bolo pravidlo drop none dominance

!------ 5. big O : o(1)
? toto je naše dalšie big o


*/

/*

! jedna sa o naše prve n kde sa počet operaci nemeni na zaklade zmeny vstupu teda nka
? v tomto pripade pokial by nko bolo 1 tak by sme mali len jednu operaciu ktora by bola sčitanie
? ale pokial by n bolo i milion stale by sme mali jednu operaciu
! a teda vysledkom je o ( 1 )
? podme to reprezentovať na grafe je položeny na xovej osy
! je to to najviac efektivne big o
? nakolko ako s n meni teda as the n becomes larger the number of the operations does not change

int addItem(int n)
{
    return n + n;
    return n + n + n; // ! čo ak by sme mali toto, o vysledku su to dve operacie teda O(2) ale stale to budeme volat o (1), duo to rule of simplification


}

!------ o of the (log n)

pre demonštraciu si zoberieme sortnutu array
demonštrujeme to na najefektivnejšej možnosti ako najst urcite čislo
mame list rozdelime ho na dve polovice
kladieme otazku je to v prvej polke alebo to je v polke druhej
a toto robime repetetivne pokial nedojde k nalezu

? super budme teda spoločne ratat how many steps sme museli zrealizovať pre najdenie toho čisla
it was three steps

nakolko sa jedna o nlog tak teda hovorime 2 na tretiu je prosto a len 8
? je to totožne ako povedať log2 of 8 = 3

hovorime two to the what power equals to 8

ked mam log2 of 8 = tak sa pytam kolkokrat musim dvojkou vydelit 8čku = trikrat

? skutočna sila tohoto je ked mame velmi velke čisla

log2 of a bilion tak sa pytame kolkokrat musime seknut aby sme sa dostali na jeden item 31 krat

teda pokial robime process repetetivneho cuttovania tak sme schopny najst akekolvek čislo čo je teda silou O (log n)

? ako to vyzera na grafe
je to velmi flat skoro ako o of(1)

! je to omnoho viac efektivne než o of(N2) alebo o of (n)

o of n2, o of n, o of (1) and the o of the log n === bude tie najčastejšie ktore uvidime



!! ešte jeden je o ( n log n ) === ktory je vyuzivany a pouzivany nijakymi sorting algoritmami napr taky merge sort alebo quick sort
? na grafe sa nachadza niekde medzi of n2 a o of n
! a to je most efficient ako sa da urobiť sorting alg


! ------ big o : different terms for inputs


/*

! niečo čo už pozname teda for loop followed by another for loop kazdy z nich runnuje n times
takze to bude = n + n = 2 n aplikujeme pravidlo drop the constants a dostaveme o (n)

void suka(int a, int b) { // miesto nka pastneme dva parametre

? dostavame teda ze prvy for loop bude runnovať a times = napr a = 8
? dostavame teda ze druhy for loop bude runnovať b times = b = rovnat 9


 for (size_t i{0}; i < n; i++)
    {
            cout << i << endl;
    }

    for(int a{0}; a < n; a++){

            cout << a << endl;
    }
}

? rozdielom medzi int n and the int a, int b
ze dostavame dva rozdielne
chybu ktoru ludia robia je ze daju check na for loop and they simply say it is the o of n
! korektne musime povedať ze prvy for loop je o of (a) + o of (b)
? najviac ako sa to da zjednodušiť je o ( a + b )


? podobne tak pokial mame forloop vo forloope teda inak povedane nested one = o ( a * b )

!! zapamatat tieto variables musime ukazať separatne musime zrealizovať different terms for inputs


!----- big o for vectors this also applies for the arrays

it usually looks like : [11,3,23,7] = kde na nultom indexe je 11 and so on plus one for the incrementing of the indexes


?? nazveme myVector and lets take a look for variety of things what we can do with the vectors
1. myVector.pushBack(2)

*/

int main(int args, char *argv[])
{

    // z pohladu big (o) pre arraye alebo vectory
    // ? nko je teda počet elementov, prvko v array alebo teda v liste

    // ? aby sme addli niečo na koniec nemusime touchnuť nič z ostatnych itemov

    std::vector<int> myVector = {11, 3, 23, 7};
    myVector.push_back(12);
    myVector.pop_back();              // znamena to ze posledny item bude removnuty
    myVector.erase(myVector.begin()); // ! a ako parameter passneme myVector.begin = čo je vlastne začiatok
    // ? ked zrealizujeme tento ukon čo to znamena že vlastne už sa nenachazda na korektnom indexe
    // ! takze musime dekriminovať i index aby sme dostali ten spravny
    // ! podstatne musime to urobiť all the way down and touch every vector
    myVector.insert(myVector.begin(), 11); // ! totožne tak ked chceme vratiť 11 na jej totožne miesto
    // ? ako parameter to prebere na prvom mieste index (myVector.begin), je teda len pozicia a pak to prebere čo tam chceš strčiť

    // ? and because of that adding or the removing of the vector is always going to be the o(1), the constand one

    // ! nezaleži či remuvujeme zo začiatku alebo konca musime sa chytiť nasledne kazdeho kvoli indexnej uprave
    // ? this will be o of the n

    // ! so the general rule pre zapametanie je pokial pridavam alebo deletujem zo začiaktku či konca vzdy to bude o of N
    // duo to reason of all of the reindexing

    // ! ake pravidlo plati pre addovanie itemu niekde v strede

    myVector.insert(myVector.begin() + 1, 69);
    // ? begining prezentuje funckia .begin 
    // ! pokial tomu tak urobime tam kde davame čislo, index sa stane nekorektny
    // ? budeme musieť zrealizovať inkrementaciu  
    // ! becuase we have to touch all of the items opäť to bude o (n)
    // ? je tu par problemov s touto logic, big o je len worst case nie best case 
    // ! i pokial by to bolo 1/2 n, tak prosto vzdy dropujeme constants 


    // ! ------ podme sa pozriet na finding an item by the value 
    // ? looking up by the value is still of n 
    // ! ale looking up by the index, kde môžeme direktivne ist na to miesto je o(1)


    // !!!!!!! zhrnutie !!!!!!!

    /*
    
    ! dajme si graf kde n =100 
    O(1) = 1 
    O ( log n ) = 7 
    O ( n ) = 100
    o (n2) = 10 000


    ? rozdiel sa stane ešte signifikantnejšim akonahle sa stane n ešte väčšim 
    o(1 = sa meniť nebude, nie je zavysle na zmene velkosti vstupu teda nka 
      O ( 10log 100) = pytam sa teda kolkokrat moze byt desiatka v stovke ? = 10 
    
        ! so as the n grows n na druhu bude rast velmi velmi rychlo 
        takze pokial budeme napr schopy rewritnut kod tak aby bol o(n) tak to bude velke ikrimincia v efficienty of the code

        o2 = je vlastne len nested loop teda loop v loope 
        o of n je proporcional 
        o of the (log n) = pokial počujete devide and the conquer 
        o of 1 = is the constatn time 

        najčastejšie najhorši ktory vidime je o2 ( teda na druhu ) ten je v tzv horrible cattegory 
        O(n log n) = uvidime to v par sorting algoritmoch 

        common data structure algorithms operations 


        ! -------- array sorting algorithms 


    */


    for (int var : myVector)
    {
        cout << var << endl;
    }
}

void printItemsOnaDruhu(int n)
{
    for (size_t i{0}; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            cout << i << j << endl;
        }
    }

    // !takze set nested forloopov runuje o of(n2)

    // ? a single for loop runuje o of(n) for (size_t i{0}; i < n; i++)

    // cout << i << endl; // vo forloope len outputneme i
}

// ! implementacie zodpovedajucim funkciam

int addItem(int n)
{
    return n + n;
}

void printItems(int n) // ! void funkcia preberajuca ako parameter n
{
    for (size_t i{0}; i < n; i++) // ? vo funkcii mame for loop ktory runnuje n times
    {
        cout << i << endl; // vo forloope len outputneme i
    }
}

void printItemsOnaDruhu2(int n) // ! mame teda jeden for loop inside of another one
{
    for (size_t i{0}; i < n; i++) // ? vo funkcii mame for loop ktory runnuje n times
    {
        for (int j = 0; j < n; j++)
        {
            cout << i << j << endl;
        }
    }
}

// ? pravidlo pre drop constant nakolko dva for loopy kazdy sa vykona o(n) dostaneme vzorec = n + n = 2n kde dropneme constatn takze dostaneme n
void printItems2(int n) // ! void funkcia preberajuca ako parameter n
{
    for (size_t i{0}; i < n; i++) // ? vo funkcii mame for loop ktory runnuje n times
    {
        cout << i << endl; // vo forloope len outputneme i
    }

    for (size_t j{0}; j < n; j++) // ? vo funkcii mame for loop ktory runnuje n times
    {
        cout << j << endl; // vo forloope len outputneme i
    }
}



---


# Úvod do DS Vector vs LinkList

#include <iostream>
using namespace std;

int main(int args, char *argv[])
{

    // ! data structues najviac je porovnanavany k listu alebo arraye
    // ako aj vector tak aj link list su dynamicke v svojej dlžke
    // ! vector ma priamu indexiaciu kde mozno direktivne pristupit na index / toto link list mať nebude
    // ? ďalšia vec je odlišna ze narozdiel od vectoru su jendnotlive nody na rozdielnych miestach v pamati
    // ! čo budem mať linked list variable ktora pointi na prvu nodu tzv head
    // ? a bude posledna ktora sa vola tail ta pointi na nodu poslednu
    // ! a potom dalšia noda pointi na dalšiu a pak na dalšiu a potom potom posledna noda pointi na nullptr
    // ? rozdielom je prave rozhadaznie v pamati nakolko kazda z node musi vzajomne pointit na seba
    // * u arraye alebo vector su nasekane za sebou tzv vo formate continuos memory

    // ! link list big O
    // so we are going to start pout by adding the node at the end of it
    // last node is going to point at the the new added node
    // and that make the tail to point to the new node
    // pre O in this case n ig going to be the number of nodes in this linked list
    // ? nezalezi tak či bude mať 4 itemy alebo 1 000 000 items in it is going to be the same number of operations to add a node to the end
    // ! čo znamena ze sa jedna o const time teda o(1)
    // ! lets take a look at the removing of the item from the last position

    // ! linke

    // ! we need to start at the head than iterate throw that link list
    // ? dovtedy kym sa nedostaneme k pointru ktory ukazuje na danu nodu
    // ? a pak vlastne len setneme ze tail sa bude rovmať pointru ukazujucemu na danu nodu
    // ! pretoze musime iterovať cez link list robi z toho o(n)

    // ? pridavanie do link listu
    // naopak pokial chceme pridať tak stači povedať ze priadany item bude rovny head pointru
    // * a head pointer movneme na novo addnutu nodu
    // jedna sa teda o totožnu operaciu kde nezaleži na počte nodes ktore su "already in"
    // teda sa jedna o o (1) = i pri pridavani ako aj odoberani zo začiatku 


    // ! addovanie nody niekde v strede 
    // 11 –--> 3 ---> 23 ----> 7 
    // ? so we want to add the 4 right after the 23 
    // 1. preiterovať k danej node 
    // 2. pointint four nodov na rovnake miesto ako 23 
    // a nasledne nastavime 23 tak aby pointili na 4 
    // ! ale nakolko musime iterovať cez link list jedna sa O of N

     // ! odstranenie nody niekde v strede 
    // 1. dostat sa k nej musime k nej preiterovať 
    // 2 povieme ze pointer z 23 je equl pointru zo štvorky 
    // a odstranime 4 nodu 
    // ? ale opäť nakolko musime iterovať cez cele = O (n)

    // link listy nemaju build in indexy 
    // ? aby sme sa dostali k node 2, musi dojsť k iteraci od head y
    // takisto na check values musime iterovať 
    // ! pri linkliste je to vzdy o(n) či hladame by the index or by the value 

    // ! base rozdiel medzi link list a vectorom 

    // remove last = linked list je o(n) u vectoru je to o(1)

    // ked chceš dať check by the index the vector is da way 

}

---

Link List under the hood 

    // ? čo je vlastne noda

    // ! je to kombinacia value and the pointer
    // * dost podobne unordered map where you have the
    /*
    value : 4,
    next : nullptr

    nech link list vyzera takto :
    11 ---> 3 ----> 23 --->7

    ! sedmička bude podona unorder mape
    ? ale ako vytorime pointer z 7 nody na tu štvrtu

    ! link list je teda simularny setu nested unordered maps 
    ? a pak mame variable head ktora pointi na začiatok na headu 
    ? pak mame tail ktora pointi na koniec 

---

# Konštrukcia linkListu 

#include <iostream>
#include <fstream>
#include <unordered_map>
#include <vector>
#include <string>
#include <algorithm>
#include <iterator>

using namespace std;

// ! constructor for out link list
/*
funkcia append
vytvori new nodu
a addne nodu na koniec

funkcia prepand
creatne novu nodu
a insertne ju na na začiatok

inert
creatine nodu
a nasledne danu nodu vloži na zodpovedajuci index

! jedna spoločna vec ktoru maju všetky je prave create new node
? vytvorime teda separatnu classu ktora len creati nody , ked teda jedna z tychto function bude potrebovať create callne class Node

? čo je vlastne noda ? podobna unorder map

*/

class Node
{

public:
    int value{};
    Node *next;

    // ? dôvod prečo pouzivame this je jednoduchy potrebujeme jasne determinovať že sa jedna o value ktore je v member časti našej classy

    Node(int value)
    {
        this->value = value; // ? je to vlastne a len this->value je z membra, vlastne berieme niečo z vonku a assignujeeme to našej member functione
        next = nullptr;      // ? .this tam byt nemusime nemame next ako parameter funkcie
    }
};

class LinkedLIst
{

private:
    Node *head; // ? pointer to a node
    Node *tail; // ? pointer to a node
    size_t length{};

    // ? vytvormne si konštruktor

public:
    LinkedLIst(int value)
    {

        Node *newNode = new Node(value); // ? vďaka new keyworde vyhradi c++ pamät na heape, kde sa bude uchovvať objekt, nemusime teda presne determinovať jej velkosť
        head = newNode;                  // newNode, je len a len pointer ktory ukazuje na heap kde je creatnuta nova noda, čo vlastne robime je že head je tiez pointer hovorime teda ukazuj na tu istu nodu ako ukazuje newNode
        tail = newNode;                  // newNode, je len a len pointer ktory ukazuje na heap kde je creatnuta nova noda, čo vlastne robime je že head je tiez pointer hovorime teda ukazuj na tu istu nodu ako ukazuje newNode
        length = 1;                      // nakolko mame len jednu creatnutu nodu naša dlzka bude teda 1
        // čo je teda vysledkom operacie ?
        // ! adresa novo vytvoreneneho objektu
        // priradi sa do ukazovatelka NODE* newnNode
        // ? takže newNode ukazuje ukazuje na novy objekt typu Node na heape

        // ? zhrnutie
        // ! na pravej strane vytvarame vytvarame pointer ktory moze pointit na novo vytvorenu nodu niekde na heape
        // 1. mame pointer, = hovori ukazuj, new Node(value) novo vytvorena noda niekde na heape
    }
};

int main(int argc, char *argv[])
{

    LinkedLIst *myLinkedList = new LinkedLIst(4);
    // !   LinkedLIst *myLinkedList = variable name je myLinkedList, variable type je to pointer na linked list 
    // ? new LinkedLIst(4); vytvarame teda novy linkedlist niekde na heape 

    // * ked to runneme dostaveme teda nodu ktora drži int value 4, ukazuje na nu head, tail 
}


# PrintList function 

#include <iostream>
#include <fstream>
#include <unordered_map>
#include <vector>
#include <string>
#include <algorithm>
#include <iterator>

using namespace std;

// ! constructor for out link list
/*
funkcia append
vytvori new nodu
a addne nodu na koniec

funkcia prepand
creatne novu nodu
a insertne ju na na začiatok

inert
creatine nodu
a nasledne danu nodu vloži na zodpovedajuci index

! jedna spoločna vec ktoru maju všetky je prave create new node
? vytvorime teda separatnu classu ktora len creati nody , ked teda jedna z tychto function bude potrebovať create callne class Node

? čo je vlastne noda ? podobna unorder map

*/

// ! classes are being by default private in the c++

class Node
{

public:
    int value{};
    Node *next;

    // ? dôvod prečo pouzivame this je jednoduchy potrebujeme jasne determinovať že sa jedna o value ktore je v member časti našej classy

    Node(int value)
    {
        this->value = value; // ? je to vlastne a len this->value je z membra, vlastne berieme niečo z vonku a assignujeeme to našej member functione
        next = nullptr;      // ? .this tam byt nemusime nemame next ako parameter funkcie
    }
};

class LinkedLIst
{

private:
    Node *head; // ? pointer to a node
    Node *tail; // ? pointer to a node
    size_t length{};

    // ? vytvormne si konštruktor

public:
    void printList()
    {
        Node *temp = head;      // ukazujeme teda na prvu
        while (temp != nullptr) // ! mohlo by byt aj len temp teda inymi slovami ak temp nie je null a ukazuje na platny objekt
        {
            cout << temp->value << endl; // ! bude sa teda jednať o hodnotu na ktoru temp pointi
            // pokial mame teda premennu ktora ukazuje na nodu, mame pristup k atributom v tej node,
            // ! atributy su value and the next
            temp = temp->next; // ! movne to temp na next nodu
        }

        // ! pri poslednej iteraci dôjde k rovnosti na nullptr, čo nas breakne z while loopu
    }

    void getHead()
    {
        cout << "This is the head : " << head->value << endl;
    }

    void getTail()
    {
        cout << "This is the head : " << head->value << endl;
    }

    void getLength()
    {
        cout << "This is the head : " << length << endl;
    }

    LinkedLIst(int value)
    {

        Node *newNode = new Node(value); // ? vďaka new keyworde vyhradi c++ pamät na heape, kde sa bude uchovvať objekt, nemusime teda presne determinovať jej velkosť
        head = newNode;                  // newNode, je len a len pointer ktory ukazuje na heap kde je creatnuta nova noda, čo vlastne robime je že head je tiez pointer hovorime teda ukazuj na tu istu nodu ako ukazuje newNode
        tail = newNode;                  // newNode, je len a len pointer ktory ukazuje na heap kde je creatnuta nova noda, čo vlastne robime je že head je tiez pointer hovorime teda ukazuj na tu istu nodu ako ukazuje newNode
        length = 1;                      // nakolko mame len jednu creatnutu nodu naša dlzka bude teda 1
                                         // čo je teda vysledkom operacie ?
                                         // ! adresa novo vytvoreneneho objektu
                                         // priradi sa do ukazovatelka NODE* newnNode
                                         // ? takže newNode ukazuje ukazuje na novy objekt typu Node na heape

        // ? zhrnutie
        // ! na pravej strane vytvarame vytvarame pointer ktory moze pointit na novo vytvorenu nodu niekde na heape
        // 1. mame pointer, = hovori ukazuj, new Node(value) novo vytvorena noda niekde na heape
    }
};

int main(int argc, char *argv[])
{

    LinkedLIst *myLinkedList = new LinkedLIst(4);
    // !   LinkedLIst *myLinkedList = variable name je myLinkedList, variable type je to pointer na linked list
    // ? new LinkedLIst(4); vytvarame teda novy linkedlist niekde na heape

    // * ked to runneme dostaveme teda nodu ktora drži int value 4, ukazuje na nu head, tail
    myLinkedList->getHead();
    myLinkedList->getTail();
    myLinkedList->getLength();
    myLinkedList->printList();

    /*

    ! požadovany vystup

    This is the head : 4
    This is the head : 4
    This is the head : 1
    4



    */
}


# LinkList destructor 

~LinkedLIst() // ! hovorime teda o deštruktore
    {
        Node *temp = head;
        while (head != nullptr)
        {
            head = head->next; // muvnutie
            delete temp;       // vymaze to prvu nodu
            temp = head;       // opätovne potom musime posunuť temp aby bol rovny heade
        }
    }
    // ! head, tail, length = nie su mazane tymto deštruktorom, su mazane dštruktorom which is called the base one
};

int main(int argc, char *argv[])
{

    LinkedLIst *myLinkedList = new LinkedLIst(4);
    // ! new keyword znamena, že budeme runnovať konštruktor pre classu LinkedList

    // delete myLinkedList
    // ! to by runnuť deštruktor pre classu, čo sa však stane pokial kod pre deštruktor nemame definovny runne to ten deafultny

    // ? čo by sa stalo pokiaľ by sme runnuli defaultny constructor

    /*
    Su tu dve rozdielne classy ktore tvoria tento linkList je tu LinkedLIst a je tu Node class
    vymaze to len head, tail a length... avšak u node nevie ako ich odstraniť, teda všetky nody ostanu v pamäti

    */
}



# LinkList append 

  void append(int value)
    {
        Node *newNode = new Node(value); // ! first thing which we need to do is to create the node

        if (head == nullptr) // ak je teda zoznam prazdny alebo if(length == 0 )
        {
            head = newNode; // novy uzol je prvy a zaroven posledny
            tail = newNode;
        }
        else // ? this is for when we have items in our link list
        {
            tail->next = newNode; // ? ukazovatel posledneho uzla bude teraz ukazovať na novy uzol
            tail = newNode;       // tail sa posunie na uzol noby
        }

        length++;
    }

int main(int argc, char *argv[])
{

    LinkedLIst *myLinkedList = new LinkedLIst(4);
    myLinkedList->append(5);
    myLinkedList->printList();

}





