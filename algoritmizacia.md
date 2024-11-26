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
