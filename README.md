
# Adicionando conteúdos no Navigation Drawer em app android

## Descrição

Projeto simples que visa adicionar conteúdos na navigation drawer 

## Capturas de Tela

![image](https://github.com/AnnaKarolineNunes/NavigationDrawer/assets/101477642/6371a011-1518-4e77-99ed-d86b26fab6a4)


## Passo a passo

- Passo 1 : criar um novo item de menu no arquivo navigation drawer. Neste caso duplicamos um item e alteramos o id, icone e title
  ```
   <group android:checkableBehavior="single">
        <item
            android:id="@+id/nav_home"
            android:icon="@drawable/ic_menu_home_24dp"
            android:title="@string/menu_home" />
        <item
            android:id="@+id/nav_gallery"
            android:icon="@drawable/ic_menu_gallery"
            android:title="@string/menu_gallery" />
        <item
            android:id="@+id/nav_slideshow"
            android:icon="@drawable/ic_menu_slideshow"
            android:title="@string/menu_slideshow" />
        <item
            android:id="@+id/nav_tools"
            android:icon="@drawable/ic_menu_manage"
            android:title="@string/menu_tools" />
        // adicionamos o item contato
        <item
            android:id="@+id/nav_contato"
            android:icon="@drawable/ic_menu_email"
            android:title="@string/menu_contato" />
    </group>
- Passo 2  Para se manter um padrão de organização,  duplicamos um item dentro do arquivo strings.xml e mudamos o texto que irá aparecer dentro do novo item.
  ```
        <resources>
            <string name="app_name">NavigationDrawer</string>
            <string name="navigation_drawer_open">Open navigation drawer</string>
            <string name="navigation_drawer_close">Close navigation drawer</string>
            <string name="nav_header_title">Android Studio</string>
            <string name="nav_header_subtitle">android.studio@android.com</string>
            <string name="nav_header_desc">Navigation header</string>
            <string name="action_settings">Settings</string>
        
            <string name="menu_home">Home</string>
            <string name="menu_gallery">Galeria</string>
            <string name="menu_slideshow">Apresentaçao</string>
            <string name="menu_tools">Ferramentas</string>
            <string name="menu_share">Compartilhar</string>
            <string name="menu_send">Enviar</string>
            // adicionamos esse item
            <string name="menu_contato">Contato</string>
        </resources>

- Passo 3   Adicionar  o id criado dentro do arquivo MainActivity.java
  ```
  // dentro do método AppBarConfiguration, adicionamos o id criado:
  mAppBarConfiguration = new AppBarConfiguration.Builder(
                R.id.nav_home, R.id.nav_gallery, R.id.nav_slideshow,
                R.id.nav_tools, R.id.nav_share, R.id.nav_send, R.id.nav_contato) 
                .setDrawerLayout(drawer)
                .build();

- Passo 4  Criar o fragment do id criado  dentro da pasta. Para isso, crie um pacote dentro da pasta ui com o nome do item.
- Passo 5 Criar um fragment em branco
- Passs 6 No arquivo xml, mude para constraint layout se ainda nao estiver
  ```
  <?xml version="1.0" encoding="utf-8"?>
    <androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:tools="http://schemas.android.com/tools"
      android:layout_width="match_parent"
      android:layout_height="match_parent"
      tools:context=".ui.contato.ContatoFragment">
  
      <!-- TODO: Update blank fragment layout -->
      <TextView
          android:layout_width="match_parent"
          android:layout_height="match_parent"
          android:text="@string/hello_blank_fragment" />
    </androidx.constraintlayout.widget.ConstraintLayout>

- Passs 7 Edite o layout da forma que preferir

- Passo 8 Dentro das pastas app/src/main/res/navigation abra o arquivo mobile_navigation.xml e adicione um item do tipo fragment para que o item passe a ser clicável
  ```
    <fragment
        android:id="@+id/nav_home"
        android:name="com.cursoandroid.navigationdrawer.ui.home.HomeFragment"
        android:label="@string/menu_home"
        tools:layout="@layout/fragment_home" />
  

