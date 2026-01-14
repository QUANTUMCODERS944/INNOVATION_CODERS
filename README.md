 #include <stdio.h>
 #define DCOUNT 11
#define MCOUNT 20

typedef struct { char title[50]; char signs[200];
char precaution[200]; char meds[3][50];
int medTotal;
} Illness;

typedef struct { char label[50];
char amount[100]; char risks[200];
char forIllness[3][50]; int illTotal;
} Tablet;

int text_length(const char *t){

int i=0; while(t[i]!=0) i++; return i;
}

void data_copy(char *to, const char *from){ int p=0;
while(from[p]!=0){
to[p]=from[p]; p++;
}
to[p]=0;
}

int text_match(const char *x, const char *y){ int a=0;
while(x[a]!=0 && y[a]!=0){ char c1=x[a], c2=y[a];
if(c1>='A' && c1<='Z') c1 = c1 - 'A' + 'a';
if(c2>='A' && c2<='Z') c2 = c2 - 'A' + 'a';
if(c1!=c2) return (c1>c2)?1:-1; a++;
}
if(x[a]==0 && y[a]==0) return 0; return (x[a]==0)?-1:1;
}

void cut_newline(char *t){ int i=0;
while(t[i]!=0){ if(t[i]=='\n' || t[i]=='\r'){
t[i]=0;
return;
} i++;

}
}

void put_illness(Illness arr[]){ data_copy(arr[0].title,"Fever");
data_copy(arr[0].signs,"High body heat, weakness, tired feeling."); data_copy(arr[0].precaution,"Drink warm water, rest, avoid cold
food.");
data_copy(arr[0].meds[0],"Paracetamol"); data_copy(arr[0].meds[1],"Ibuprofen"); arr[0].medTotal=2;

data_copy(arr[1].title,"Cold");
data_copy(arr[1].signs,"Sneezing, nose block, mild headache."); data_copy(arr[1].precaution,"Stay warm, avoid cold drinks."); data_copy(arr[1].meds[0],"Cetirizine"); data_copy(arr[1].meds[1],"Paracetamol");
arr[1].medTotal=2;

data_copy(arr[2].title,"Allergy"); data_copy(arr[2].signs,"Itchy skin, rashes, watery eyes."); data_copy(arr[2].precaution,"Avoid dust and allergens."); data_copy(arr[2].meds[0],"Cetirizine");
arr[2].medTotal=1;

data_copy(arr[3].title,"Headache");  data_copy(arr[3].signs,"Pain in head, pressure feeling."); data_copy(arr[3].precaution,"Rest in dark room, avoid stress."); data_copy(arr[3].meds[0],"Ibuprofen"); data_copy(arr[3].meds[1],"Paracetamol");
arr[3].medTotal=2;

data_copy(arr[4].title,"Diabetes"); data_copy(arr[4].signs,"Tiredness, frequent urination, thirst."); data_copy(arr[4].precaution,"Avoid sugar, regular walk.");

data_copy(arr[4].meds[0],"Metformin"); arr[4].medTotal=1;

data_copy(arr[5].title,"Epilepsy"); data_copy(arr[5].signs,"Dizziness,loss of consciousness,muscle
stiffening");
data_copy(arr[5].precaution,"Avoid lack of Sleep,Alcohol,Avoid triggers");
data_copy(arr[5].meds[0],"Levera 500"); arr[5].medTotal=1;

data_copy(arr[6].title,"Dengue"); data_copy(arr[6].signs,"High Fever,Severe
Headache,Vomitting,Rash"); data_copy(arr[6].precaution,"Prevent Mosquito bites,Remove
stagnant Water,Use Mosquito Repellents"); data_copy(arr[6].meds[0],"Paracetamol"); data_copy(arr[6].meds[1],"ORS");
data_copy(arr[6].meds[2],"No NSAIDs(avoid aspirin/ibuprofen)"); arr[6].medTotal=3;

data_copy(arr[7].title,"Typhoid"); data_copy(arr[7].signs,"Persistent Fever,Abdominal
Pain,Weakness,Loss of Apetite"); data_copy(arr[7].precaution,"Drink clean Water,Maintain
Hygiene,Avoid Street Food"); data_copy(arr[7].meds[0],"Azithromycin"); data_copy(arr[7].meds[1],"ORS"); arr[7].medTotal=2;

data_copy(arr[8].title,"Tuberculosis"); data_copy(arr[8].signs,"Long Lasting Cough,Weight Loss,Night
Sweats,Mild Fever");
data_copy(arr[8].precaution,"Avoid Close Contact when suffering from disease,Good Ventilation,Mask and Hygiene");

data_copy(arr[8].meds[0],"Anti TB regimen(HRZE"); arr[8].medTotal=1;

data_copy(arr[9].title,"Hypertension"); data_copy(arr[9].signs,"Headache,Sometimes Dizziness"); data_copy(arr[9].precaution,"Low Salt Diet,Excercise,Stress
Control"); data_copy(arr[9].meds[0],"TELMED CT");
data_copy(arr[9].meds[1],"TAZOLAC-AM 40"); data_copy(arr[9].meds[2],"Amlopdipine"); arr[9].medTotal=3;

data_copy(arr[10].title,"Asthma"); data_copy(arr[10].signs,"Wheezing,Shortness of Breath,Chest
Tightness");
data_copy(arr[10].precaution,"Avoid dust,smoke,Use inhaler regularly,Stay away from the Allergens");
data_copy(arr[10].meds[0],"Steroid Inhalers"); data_copy(arr[10].meds[1],"Inhaled bronchodilators"); arr[10].medTotal=2;
}

void put_medicines(Tablet arr[]){ data_copy(arr[0].label,"Paracetamol"); data_copy(arr[0].amount,"500 mg two times daily."); data_copy(arr[0].risks,"Can upset stomach if empty stomach."); data_copy(arr[0].forIllness[0],"Fever"); data_copy(arr[0].forIllness[1],"Cold"); data_copy(arr[0].forIllness[2],"Headache");
arr[0].illTotal=3;

data_copy(arr[1].label,"Ibuprofen"); data_copy(arr[1].amount,"400 mg once or twice daily."); data_copy(arr[1].risks,"May cause acidity or dizziness."); data_copy(arr[1].forIllness[0],"Fever");

data_copy(arr[1].forIllness[1],"Headache"); arr[1].illTotal=2;

data_copy(arr[2].label,"Cetirizine"); data_copy(arr[2].amount,"10 mg before sleep."); data_copy(arr[2].risks,"Can cause sleepiness."); data_copy(arr[2].forIllness[0],"Cold"); data_copy(arr[2].forIllness[1],"Allergy"); arr[2].illTotal=2;

data_copy(arr[3].label,"Metformin"); data_copy(arr[3].amount,"500 mg twice a day with food."); data_copy(arr[3].risks,"Can cause stomach discomfort at start."); data_copy(arr[3].forIllness[0],"Diabetes");
arr[3].illTotal=1;

data_copy(arr[4].label,"Levera 500"); data_copy(arr[4].amount,"500 mg twice daily."); data_copy(arr[4].risks,"May cause dizziness and behaviours
changes"); data_copy(arr[4].forIllness[0],"Epilepsy"); arr[4].illTotal=1;

data_copy(arr[5].label,"VitaminC"); data_copy(arr[5].amount,"500 mg once daily."); data_copy(arr[5].risks,"May cause gas if empty stomach."); data_copy(arr[5].forIllness[0],"Cold");
arr[5].illTotal=1;

data_copy(arr[6].label,"Metformin"); data_copy(arr[6].amount,"500-850 mg twice daily."); data_copy(arr[6].risks,"May cause Acidity and Nausea"); data_copy(arr[6].forIllness[0],"Diabetes"); arr[6].illTotal=1;

data_copy(arr[7].label,"Glimepiride"); data_copy(arr[7].amount,"1-2 mg once daily"); data_copy(arr[7].risks,"Posseses risks of Hypolglycemia"); data_copy(arr[7].forIllness[0],"Diabetes");
arr[7].illTotal=1;

data_copy(arr[8].label,"Carbamazepine"); data_copy(arr[8].amount,"200 mg twice daily."); data_copy(arr[8].risks,"May cause Dizziness,Liver Effects"); data_copy(arr[8].forIllness[0],"Epilepsy");
arr[8].illTotal=1;

data_copy(arr[9].label,"Crocin");
data_copy(arr[9].amount,"500 mg once daily if suffering(SOS)"); data_copy(arr[9].risks,"Not advisable without Doctors's
recommendation."); data_copy(arr[9].forIllness[0],"Cold"); data_copy(arr[9].forIllness[1],"Fever"); arr[9].illTotal=2;

data_copy(arr[10].label,"Isoniazid(INH)"); data_copy(arr[10].amount,"300 mg ONCE daily."); data_copy(arr[10].risks,"May cause Nerve issues,Liver Damage"); data_copy(arr[10].forIllness[0],"Tuberculosis");
arr[10].illTotal=1;

data_copy(arr[11].label,"Rifampicin"); data_copy(arr[11].amount,"450-600 mg once daily"); data_copy(arr[11].risks,"Can possess the threat of Orange urine,
Liver strain"); data_copy(arr[11].forIllness[0],"Tuberculosis"); arr[11].illTotal=1;

data_copy(arr[12].label,"Azithromycin");

data_copy(arr[12].amount,"500 mg day 1,then 250 mg for 2-4 days");
data_copy(arr[12].risks,"May cause Nausea,Loose Motion"); data_copy(arr[12].forIllness[0],"Cold(Bacterial)"); data_copy(arr[12].forIllness[1],"Typhoid");
arr[12].illTotal=2;

data_copy(arr[13].label,"Salbutamol Inhaler"); data_copy(arr[13].amount,"1-2 puffs during attack"); data_copy(arr[13].risks,"Fast Heartbeat and Tremors"); data_copy(arr[13].forIllness[0],"Asthma"); arr[13].illTotal=1;

data_copy(arr[14].label,"Amplodipine"); data_copy(arr[14].amount,"5-10 mg once daily"); data_copy(arr[14].risks,"Swelling of Feet"); data_copy(arr[14].forIllness[0],"Hyper Tension"); arr[14].illTotal=1;

data_copy(arr[15].label,"Aceclofenac"); data_copy(arr[15].amount,"100 mg twice Daily"); data_copy(arr[15].risks,"May cause Gastric irritaion and Acidity"); data_copy(arr[15].forIllness[0],"Fever"); data_copy(arr[15].forIllness[1],"Headache"); data_copy(arr[15].forIllness[2],"Allergy related body pain"); arr[15].illTotal=3;

data_copy(arr[16].label,"Levocetrizine"); data_copy(arr[16].amount,"5 mg once daily"); data_copy(arr[16].risks,"May cause Drowsiness and Dizziness"); data_copy(arr[16].forIllness[0],"Cold"); data_copy(arr[16].forIllness[1],"Allergy");
arr[16].illTotal=2; data_copy(arr[17].label,"Montelukast");

data_copy(arr[17].amount,"10 mg once daily(usually at night)"); data_copy(arr[17].risks,"May cause Mood Changes and
Headache"); data_copy(arr[17].forIllness[0],"Allergy"); data_copy(arr[17].forIllness[1],"Asthma"); arr[17].illTotal=2;

data_copy(arr[18].label,"Diclofenac"); data_copy(arr[18].amount,"50 mg twice daily"); data_copy(arr[18].risks,"Risk of Gstric Ulser"); data_copy(arr[18].forIllness[0],"HeadAche"); data_copy(arr[18].forIllness[1],"Body pain"); arr[18].illTotal=2;

data_copy(arr[19].label,"Cefixime"); data_copy(arr[19].amount,"12.5-25 mg once daily"); data_copy(arr[19].risks,"May cause Diarrhoea and Stomach
upset"); data_copy(arr[19].forIllness[0],"Typhoid");
data_copy(arr[19].forIllness[1],"Cold(bacterial)"); data_copy(arr[19].forIllness[2],"Fever with infection"); arr[19].illTotal=3;

}

void showMedicine(Tablet t){ int j;
printf("\n=== MEDICINE INFORMATION ===\n");
printf("Name: %s\n",t.label); printf("Dosage: %s\n",t.amount); printf("Side Effects: %s\n",t.risks); printf("Used For:\n"); for(j=0;j<t.illTotal;j++){
printf(" - %s\n",t.forIllness[j]);
}

}

void listAllIllness(Illness arr[]){ int i;
printf("\n--- ALL ILLNESSES ---\n"); for(i=0;i<DCOUNT;i++){
printf("%d. %s\n",i+1,arr[i].title);
}
}

void listAllMedicines(Tablet arr[]){ int i;
printf("\n--- ALL MEDICINES ---\n"); for(i=0;i<MCOUNT;i++){
if(text_length(arr[i].label)>0) printf("%d. %s\n",i+1,arr[i].label);
}
}

void findAllMedicinesForIllness(char *illName, Tablet med[]){ int i,j;
printf("\nMedicines linked to this illness:\n"); for(i=0;i<MCOUNT;i++){
for(j=0;j<med[i].illTotal;j++){ if(text_match(med[i].forIllness[j],illName)==0){
printf(" - %s\n",med[i].label); break;
}
}
}
}

void showFullDatabase(Illness ill[], Tablet med[]){ int i;
printf("\n====== FULL DATABASE ======\n");

for(i=0;i<DCOUNT;i++){
printf("\nIllness: %s\nSymptoms: %s\nPrecaution:
%s\n",ill[i].title,ill[i].signs,ill[i].precaution);
}
printf("\n--- Medicines ---\n"); for(i=0;i<MCOUNT;i++){
if(text_length(med[i].label)>0) printf("%s - %s -
%s\n",med[i].label,med[i].amount,med[i].risks);
}
}

void showInstructions(){
printf("\n=== HOW TO USE MEDTRACK ===\n");
printf("1. Search illnesses by name.\n"); printf("2. Search medicines by name.\n");
printf("3. Illness information includes its medicines.\n"); printf("4. Medicine information includes diseases it treats.\n");
}

void searchMedicine(Tablet arr[]){ char word[50];
int i;
char again[10];

while(1){
printf("\nEnter medicine name: "); if(fgets(word,50,stdin)==NULL) return; cut_newline(word);

for(i=0;i<MCOUNT;i++){
if(text_length(arr[i].label)>0 && text_match(arr[i].label,word)==0){
showMedicine(arr[i]); break;

}
}

if(i==MCOUNT){
printf("No such medicine found.\n");
}

while(1){
printf("\nDo you want to search another medicine? (yes/no): "); if(fgets(again,10,stdin)==NULL) return;
cut_newline(again); if(text_length(again)==0) continue; if(text_match(again,"yes")==0) break; if(text_match(again,"no")==0) return; printf("Please answer yes or no.\n");
}
}
}

void showIllness(Illness d, Tablet med[]){ int j;
char ask[10];

printf("\n=== ILLNESS INFORMATION ===\n");
printf("Name: %s\n",d.title); printf("Symptoms: %s\n",d.signs); printf("Precautions: %s\n",d.precaution); printf("Medicines:\n"); for(j=0;j<d.medTotal;j++){
printf(" - %s\n",d.meds[j]);
}

findAllMedicinesForIllness(d.title,med); while(1){

printf("\nDo you want to know about any medicine from this list? (yes/no): ");
if(fgets(ask,10,stdin)==NULL) return; cut_newline(ask); if(text_length(ask)==0) continue;

if(text_match(ask,"yes")==0){ searchMedicine(med); return;
}
if(text_match(ask,"no")==0){ return;
}

printf("Please answer yes or no.\n");
}
}

void searchIllness(Illness arr[], Tablet med[]){ char word[50];
int i;

printf("\nEnter illness name: "); if(fgets(word,50,stdin)==NULL) return; cut_newline(word);

for(i=0;i<DCOUNT;i++){
if(text_match(arr[i].title,word)==0){ showIllness(arr[i],med);
return;
}
}
printf("No such illness found.\n");
}

int main(){
Illness ill[DCOUNT]; Tablet med[MCOUNT]; int pick, dump;

put_illness(ill); put_medicines(med);

while(1){
printf("\n--- MEDTRACK MENU ---\n"); printf("1. Search Illness\n");
printf("2. Search Medicine\n"); printf("3. List All Illnesses\n"); printf("4. List All Medicines\n"); printf("5. Full Database View\n"); printf("6. Instructions\n"); printf("7. Exit\n");
printf("Choose: ");

if(scanf("%d",&pick)!=1){ while((dump=getchar())!='\n' && dump!=EOF); continue;
}
while((dump=getchar())!='\n' && dump!=EOF);

if(pick==1) searchIllness(ill,med);
else if(pick==2) searchMedicine(med); else if(pick==3) listAllIllness(ill);
else if(pick==4) listAllMedicines(med);
else if(pick==5) showFullDatabase(ill,med); else if(pick==6) showInstructions();
else if(pick==7){ printf("Goodbye.\n"); break;
}

else printf("Invalid choice.\n");
}

return 0;
}



