# programs third month
---

**Activity и Intents:**
**Activity** - это компонент приложения в **Android,** который представляет собой экран пользовательского интерфейса. Каждая **Activity** имеет свое собственное окно, которое отображается на экране устройства. Для перехода между **Activity** используются **Intents.** **Intents** - это объекты, которые используются для связи между компонентами приложения. Они могут быть использованы для запуска новой **Activity** или для передачи данных между **Activity.**

---

Пример кода для создания нового **Intent** и запуска другой **Activity:**

**Intent intent = new Intent(MainActivity.this, SecondActivity.class);**
**startActivity(intent);**

---

В этом примере мы создали новый объект **Intent** и указали, что мы хотим запустить **SecondActivity.** Затем мы вызываем метод **startActivity(),** чтобы запустить **Activity.**

**Fragment:**
**Fragment** - это компонент приложения в **Android,** который представляет собой часть пользовательского интерфейса. Фрагменты могут быть использованы для создания многих различных интерфейсов на одном экране. Они также могут использоваться для создания переиспользуемых компонентов пользовательского интерфейса. Фрагменты обычно используются в сочетании с **Activity.**

---

Пример кода для создания фрагмента:

**public class MyFragment extends Fragment {**

    @Override
    public View onCreateView(LayoutInflater inflater, ViewGroup container, Bundle savedInstanceState) {
       // Инфлейтим макет фрагмента
        View view = inflater.inflate(R.layout.my_fragment_layout, container, false;
        // Возвращаем созданный View
        return view;
    }

**}**

---

В этом примере мы создали новый фрагмент **MyFragment,** который инфлейтит макет **my_fragment_layout.** Затем мы возвращаем созданный **View.**

**RecyclerView:**
**RecyclerView** - это компонент пользовательского интерфейса в **Android,** который используется для отображения списка элементов с возможностью прокрутки. **RecyclerView** позволяет отображать большие наборы данных в списке, не загружая их все сразу. Он также позволяет создавать настраиваемые элементы списка.

---

Пример кода для создания **RecyclerView:**

**public class MyActivity extends AppCompatActivity {**

**private RecyclerView mRecyclerView;**

---

**private MyAdapter mAdapter;**

---

**private RecyclerView.LayoutManager mLayoutManager;**

---

**@Override**
**protected void onCreate(Bundle savedInstanceState) {**
**super.onCreate(savedInstanceState);**
**setContentView(R.layout.my_activity_layout);**

---

**mRecyclerView = findViewById(R.id.my_recycler_view);**
**mRecyclerView.setHasFixedSize(true);**
**mLayoutManager = new LinearLayoutManager(this);**
**mRecyclerView.setLayoutManager(mLayoutManager);**
**mAdapter = new MyAdapter(myDataset);**
**mRecyclerView.setAdapter(mAdapter);**
**}**
**}**

---

В этом примере мы создали **RecyclerView,** установили ему фиксированный размер, установили **LayoutManager,** который будет управлять расположением элементов, и установили адаптер, который будет заполнять элементы данными.

---

ViewBinding - это механизм в Android, который позволяет связывать Views в макете с переменными в коде. С помощью ViewBinding вы можете избежать необходимости использовать метод findViewById() для поиска Views в макете.

---

Пример кода для использования ViewBinding:

public class MyActivity extends AppCompatActivity {

    private ActivityMyBinding binding;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        binding = ActivityMyBinding.inflate(getLayoutInflater());
        setContentView(binding.getRoot());

        binding.myTextView.setText("Hello World!");
    }
}

---

В этом примере мы использовали **ViewBinding** для связывания **TextView** с идентификатором **myTextView** в макете с переменной **binding** в коде. Затем мы установили текст для **TextView.**

---

**Kotlin:**
**Kotlin** - это язык программирования, разработанный **JetBrains,** который работает на платформе **Java.** **Kotlin** - это статически типизированный язык, который имеет функциональные и объектно-ориентированные возможности.

Основное отличие **Kotlin** от **Java** заключается в том, что **Kotlin** имеет более компактный синтаксис и более безопасную типизацию. **Kotlin** также имеет множество встроенных функций и возможностей, которые делают код более лаконичным и выразительным.

---

Пример кода на **Kotlin:**

**data class Person(val name: String, val age: Int)**

**val person = Person("John Doe", 30)**
**println("Name: ${person.name}, Age: ${person.age}")**
В этом примере мы определили класс **Person** с помощью ключевого слова **data class.** Затем мы создали новый объект **Person** и распечатали его свойства.

**Data Classes, Open Classes, Inner Classes:**
**Data Classes** - это классы, которые создаются для хранения данных. Они автоматически генерируют методы **equals(), hashCode() и toString()** на основе свойств класса.

---

Пример кода на **Kotlin** для создания **Data Class:**

**data class Person(val name: String, val age: Int)**
**Open Classes** - это классы, которые можно наследовать. В **Kotlin** все классы являются по умолчанию **final,** что означает, что они не могут быть наследованы. Чтобы класс можно было наследовать, нужно объявить его как **open.**

---

Пример кода на **Kotlin** для создания **Open Class:**


**open class Person(val name: String, val age: Int)**
**Inner Classes** - это классы, которые объявлены внутри другого класса. Они могут быть использованы для создания связанных классов, которые могут иметь доступ к приватным свойствам и методам родительского класса.

---

Пример кода на **Kotlin** для создания **Inner Class:**

**class Outer {**
**private val bar: Int = 1**
**inner class Inner {**
**fun foo() = bar**
**}**
**}**

---

примере мы определили класс **Outer,** который имеет свойство **bar** и вложенный класс **Inner.** В **Inner** классе мы объявили метод **foo(),** который возвращает значение свойства **bar** родительского класса **Outer.**

Таким образом, мы можем создать экземпляр **Inner** класса и получить доступ к свойству **bar** родительского класса через метод **foo():**

**val outer = Outer()**
**val inner = outer.Inner()**
**println(inner.foo()) // выведет: 1**

Также **Inner** классы могут иметь доступ к приватным свойствам и методам родительского класса. Это может быть полезно, когда нам нужно создать класс, который имеет доступ к частным свойствам родительского класса, но не должен быть доступен извне.

---

Кроме того, **Inner** класс может иметь свои собственные свойства и методы, которые не зависят от родительского класса. **Inner** класс может также наследовать от других классов, реализовать интерфейсы и переопределять методы родительского класса.

Например, рассмотрим следующий пример с вложенным классом, который наследуется от другого класса:

**class Outer {**
**private val bar: Int = 1**
**inner class Inner : BaseClass() {**
**fun foo() = bar + super.baz()**
**}**
**}**

**open class BaseClass {**
**open fun baz() = 0**
**}**

**val outer = Outer()**
**val inner = outer.Inner()**
**println(inner.foo()) // выведет: 2**

---
