# Data-Structures-Project
import java.util.*;

public class IntLinkedList implements List {
private IntListNode front;
private int size;

public IntLinkedList(){
front=null;
size=0;
}

public String toString(){
if(size==0) return "[]";
IntListNode current=front;
String result="[";
 while(current!=null){
 result+=current.data+", ";
 current=current.next;
 }
 result=result.substring(0,result.length()-2)+"]";
 return result;
}

public void add(int a){
size++;
if(front==null){
front=new IntListNode(a);
}else{ 
IntListNode current=front;
while(current.next!=null){
current=current.next;
}
current.next=new IntListNode(a);
}
}

public void set(int index,int number){
IntListNode current=front;
 for(int i=0; i<index; i++){
current=current.next;
 }
current.data=number;
} 
public int remove(int index){
int result;
if(index==0){
result=front.data;
front=front.next;
}else{
IntListNode current=front;
for(int j=0; j<index-1; j++){
current=current.next;
}
result=current.next.data;
current.next=current.next.next;
size--;
}
return result;
}

public void clear(){
front=null;
size=0;
}

public void compress(int k){
IntListNode current=front;
if(k>=size()){
int count=0;
while(current!=null){
count+=current.data;
current=current.next;
}
front.data=count;
front.next=null;
return;
}
while(current!=null){
int sm=0;
IntListNode temp=current;
for(int i=0; i<k; i++){
if(temp!=null){
sm+=temp.data;
temp=temp.next;
}
 }
current.data=sm;
current.next=temp;
current=temp;
}
}
public int size(){return size;}

public void add(int index,int number){
size++;
if(index==0){
front=new IntListNode(number,front);
}else{
IntListNode current=front;
for(int a=0; a<index-1; a++){
current=current.next;
}
current.next=new IntListNode(number,current.next);
 }
}
public int indexOf(int number){
int index=0;
IntListNode current=front;
while(current!=null){
 if(current.data==number) return index;
 index++;
 current=current.next;
}
return -1;
}
public int get(int index){
IntListNode current=front;
for(int k=0; k<index; k++){
current=current.next;
}
return current.data;
}

public boolean contains(int a){
return indexOf(a)>0;
}

public boolean containsAll(IntLinkedList x){
int a=0;
IntListNode current=x.front;
while(current!=null){
if(this.contains(current.data)) a++;
current=current.next;
}
return a==x.size();
}

public boolean isEmpty(){
return size==0;
}

private boolean isPrime(int n){
for(int b=2; b<n; b++){
if(n%b==0) return false;
}
return true;
}

public void removePrime(){
 while(isPrime(front.data)) front=front.next;
IntListNode current=front;
IntListNode temp=front;
while(current!=null && current.next!=null){
if(isPrime(current.next.data)) current.next=current.next.next;
 if(isPrime(current.data)) {
 temp.next=current.next;
 }else{
 temp=current;
 }
 current=current.next;
 }
 if(current!=null && isPrime(current.data)) temp.next=null;
}

public void selectionSort(){
IntListNode current=front;
while(current!=null){
IntListNode temp=current.next;
 while(temp!=null){
 if(temp.data<current.data){
 int exchange=current.data;
 current.data=temp.data;
 temp.data=exchange;
 }
 temp=temp.next;
}
current=current.next;
 }
}

public boolean isSorted(){
IntListNode temp=front;
IntListNode temp2=front.next;
while(temp!=null && temp2!=null){
 if(temp.data>temp2.data) return false;
temp2=temp2.next;
temp=temp.next;
}
return true;
}

public void bubbleSort(){
IntListNode current=front;
while(!isSorted()){
 while(current!=null){
 if(current.next.data<current.data){
 int res=current.data;
 current.data=current.next.data;
 current.next.data=res;
 }
 current=current.next;
 }
}
}
private class IntListNode {
private int data;
private IntListNode next;

public IntListNode(){
this(0,null);
}
public IntListNode(int a){
this(a,null);
}
public IntListNode(int a, IntListNode b){
this.data=a;
this.next=b;
}
}
}
