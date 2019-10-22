---
title: Настройка поведения при удалении | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.deletebehavior
helpviewer_keywords:
- Domain-Specific Language, deletion
ms.assetid: c6bf088d-52c6-4817-af45-ddae745bb5a9
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d0dcfc5724e87d57d2803b9b64a6eb121314b99
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655044"
---
# <a name="customizing-deletion-behavior"></a>Настройка функции удаления
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Удаление элемента обычно приводит также к удалению связанных элементов. Удаляются все подключенные к нему отношения и дочерние элементы. Такое поведение называется *распространением удаления*. Распространение удалений можно настраивать, например, для организации удаления дополнительных связанных элементов. Написав код программы, можно сделать распространение удалений зависимым от состояния модели. Также можно в ответ на удаление вызвать другие изменения.

 Этот раздел включает следующие подразделы:

- [Поведение при удалении по умолчанию](#default)

- [Настройка параметра распространения удаления роли](#property)

- [Переопределение закрытия удаления](#closure) — используйте этот метод, когда удаление может привести к удалению соседних элементов.

- [Использование инструкции DELETE и удаления](#ondeleting) — используйте эти методы, в которых ответ может включать другие действия, такие как обновление значения в магазине или за его пределами.

- [Правила удаления](#rules) — используйте правила для распространения обновлений любого типа в магазине, где одно изменение может привести к другим.

- [События удаления](#rules) — используйте события хранилища для распространения обновлений за пределы хранилища, например для других [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] документов.

- Отменить [Слияние](#unmerge) — используйте операцию отмены слияния, чтобы отменять операцию слияния, которая присоединяет дочерний элемент к его родителю.

## <a name="default"></a>Поведение при удалении по умолчанию
 По умолчанию распространением удалений управляют следующие правила.

- Если элемент удаляется, также все внедренные элементы удаляются. Внедренные элементы — это целевые объекты отношений внедрения, для которых этот элемент является источником. Например, если имеется отношение внедрения из **альбома** в **песню**, то при удалении определенного альбома все его песни также будут удалены.

     При этом удаление песни не ведет к удалению альбома.

- По умолчанию удаление не распространяется на ссылочные отношения. Если существует ссылочная связь, **артистплайсоналбум** от **альбома** к **исполнителю**, при удалении альбома не удаляется ни один из связанных исполнителей, а удаление исполнителя не приводит к удалению какого-либо альбома.

     При этом удаление распространяется на некоторые встроенные отношения. Например, если удаляется элемент модели, также удаляется его фигура на схеме. Элемент и фигура связаны ссылочным отношением `PresentationViewsSubject`.

- Удаляется каждое связанное с элементом отношение в исходной или целевой роли. Свойство противоположной роли элемента больше не содержит удаленный элемент.

## <a name="property"></a>Настройка параметра распространения удаления роли
 Распространение удаления можно вызывать по ссылочному отношению или из встроенного дочернего элемента на родительский.

#### <a name="to-set-delete-propagation"></a>Настройка распространения удаления

1. На схеме определения DSL выберите *роль* , которую нужно распространить на удаление. Роль представлена линией слева или справа от поля доменной связи.

    Например, если требуется указать, что при удалении альбома следует удалить связанного исполнителя, выберите роль, связанную с классом домена "Исполнитель".

2. В окно свойств задайте свойство **распространяет удаление** .

3. Нажмите клавишу F5 и убедитесь в выполнении следующих условий.

   - Когда удаляется экземпляр этого отношения, удаляется также элемент в выбранной роли.

   - Когда удаляется элемент в противоположной роли, также удаляются экземпляры этого отношения и связанные элементы в этой роли.

   Можно также увидеть параметр **распространение удаления** в окне **сведения о DSL** . Выберите доменный класс и в окне сведения о DSL откройте страницу поведение при **удалении** , нажав кнопку в боковой части окна. Параметр **Propagate** отображается для противоположной роли каждой связи. Столбец **Удалить стиль** указывает, имеет ли параметр **Propagate** значение по умолчанию, но не имеет отдельного воздействия.

## <a name="delete-propagation-by-using-program-code"></a>Распространение удаления с помощью кода программы
 Только параметры в файле определения DSL позволяют выбирать, распространять ли удаление на соседние элементы. Для реализации более сложной схемы распространения удаления можно написать код программы.

> [!NOTE]
> Чтобы добавить программный код в определение DSL, создайте отдельный файл кода в проекте **DSL** и запишите частичные определения, чтобы расширить классы в созданной папке кода. Дополнительные сведения см. [в разделе Написание кода для того, чтобы настроить предметно-](../modeling/writing-code-to-customise-a-domain-specific-language.md)ориентированный язык.

## <a name="closure"></a>Определение закрытия удаления
 Операция удаления использует класс _йоурмодел_**делетеклосуре** , чтобы определить, какие элементы нужно удалить, учитывая начальный выбор. Проходя диаграмму отношений, он циклично вызывает методы `ShouldVisitRelationship()` и `ShouldVisitRolePlayer()`. Эти методы можно переопределить. ShouldVisitRolePlayer предоставляется с удостоверением связи и элементом в одной из ролей связи. Это позволяет вернуть одно из следующих значений:

- **Виситорфилтерресулт. Yes**— элемент должен быть удален, и обход должен продолжаться, чтобы попробовать другие ссылки элемента.

- **Виситорфилтерресулт. доноткаре** — элемент не должен удаляться, если другой запрос не отвечает, что он должен быть удален.

- **Виситорфилтерресулт. Never** — элемент не должен удаляться, даже если другой запрос отвечает « **Да**», и этот обход не должен пытаться использовать другие ссылки элемента.

```
// When a musician is deleted, delete their albums with a low rating.
// Override methods in <YourDsl>DeleteClosure in DomainModel.cs
partial class MusicLibDeleteClosure
{
  public override VisitorFilterResult ShouldVisitRolePlayer
    (ElementWalker walker, ModelElement sourceElement, ElementLink elementLink,
    DomainRoleInfo targetDomainRole, ModelElement targetRolePlayer)
  {
    ArtistAppearsInAlbum link = elementLink as ArtistAppearsInAlbum;
    if (link != null
       && targetDomainRole.RolePlayer.Id == Album.DomainClassId)
    {
      // Count other unvisited links to the Album of this link.
      if (ArtistAppearsInAlbum.GetLinksToArtists(link.Album)
              .Where(linkAlbumArtist =>
                     linkAlbumArtist != link &&
                     !walker.Visited(linkAlbumArtist))
              .Count() == 0)
      {
        // Should delete this role player:
        return VisitorFilterResult.Yes;
      }
      else
        // Don’t delete unless another relationship deletes it:
        return VisitorFilterResult.DoNotCare;
    }
    else
    {
      // Test for and respond to other relationships and roles here.

      // Not the relationship or role we’re interested in.
      return base.ShouldVisitRolePlayer(walker, sourceElement,
             elementLink, targetDomainRole, targetRolePlayer);
    }
  }
}

```

 Технология замыкания гарантирует определение удаляемого набора элементов и связей перед началом удаления. Обход также объединяет результаты замыкания с результатами из других частей модели.

 В то же время данная технология предполагает, что удаление влияет только на соседние элементы в диаграмме отношений. Нельзя использовать этот метод для удаления элемента в другой части модели, а также для добавления элементов или внесения других изменений в ответ на удаление.

## <a name="ondeleting"></a>Использование инструкции DELETE и удаления
 В классе или доменной связи методы `OnDeleting()` или `OnDeleted()` переопределить нельзя.

1. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleting%2A> вызывается, когда элемент собирается удалиться, но до отключения его связей. Он по-прежнему находится в `store.ElementDirectory` и допускает переход в другие или из других элементов.

    Если несколько элементов удаляются в одно и то же время, то перед выполнением этого действия для них всех вызывается метод OnDeleting.

    `IsDeleting` имеет значение true.

2. <xref:Microsoft.VisualStudio.Modeling.ModelElement.OnDeleted%2A> вызывается при удалении элемента. Он остается в куче CLR, чтобы при необходимости можно было выполнить отмену. При это он теряет связи от другими элементами и удаляется из `store.ElementDirectory`. Для связей роли по-прежнему ссылаются на старые исполнители ролей. `IsDeleted` имеет значение true.

3. Методы OnDeleting и OnDeleted вызываются, когда пользователь запускает операцию отмены после создания элемента, а также когда предыдущее удаление повторяется в операции повтора. В таких случаях во избежание обновления элементов хранилища используйте метод `this.Store.InUndoRedoOrRollback`. Дополнительные сведения см. в разделе [инструкции. Использование транзакций для обновления модели](../modeling/how-to-use-transactions-to-update-the-model.md).

   Например, следующий код удаляет альбом, когда удаляется его последняя дочерняя песня:

```

// Delete the parent Album when the last Song is deleted.
// Override methods in the embedding relationship between Album and Song:
partial class AlbumHasSongs
{
  protected override void OnDeleted()
  {
    base.OnDeleted();
    // Don't perform in-store actions in undo:
    if (this.Store.InUndoRedoOrRollback) return;
    // Relationship source and target still work:
    // Don't bother if source is already on its way out:
    if (!this.Album.IsDeleting && !this.Album.IsDeleted)
    {
      if (this.Album.Songs.Count == 0)
      {
        this.Album.Delete();
} } } }

```

 Часто полезнее активировать триггер из удаления отношения, чем из элемента роли, так как он работает и при удалении элемента, и при удалении самого отношения. Для ссылочного отношения может распространение удаления может потребоваться при удалении связанного элемента, а не самого отношения. В этом примере альбом удаляется, когда удаляется последний указанный в нем исполнитель, но не отвечает, если удаляются отношения:

```
using System.Linq; ...
// Assumes a many-many reference relationship
// between Artist and Album.
partial class Artist
{
  protected override void OnDeleting()
  {
    base.OnDeleting();
    if (this.Store.InUndoRedoOrRollback) return;
    List<Album> toDelete = new List<Album>();
    foreach (Album album in this.Albums)
    {
      if (album.Artists.Where(artist => !artist.IsDeleting)
                        .Count() == 0)
      {
        toDelete.Add(album);
      }
    }
    foreach (Album album in toDelete)
    {
      album.Delete();
} } }

```

 Когда к элементу применяется команда <xref:Microsoft.VisualStudio.Modeling.ModelElement.Delete%2A>, вызываются методы OnDeleting и OnDeleted. Они всегда выполняются встроенным образом, т. е. непосредственно перед и сразу после фактического удаления. Если код удаляет два или несколько элементов, методы OnDeleting и OnDeleted применяются ко всем элементам по очереди.

## <a name="rules"></a>Правила удаления и события
 В качестве альтернативы обработчикам OnDelete можно настроить правила и события удаления.

1. Правила **удаления** и **удаления** активируются только в транзакции, а не в операциях отмены или повтора. Можно поместить эти правила в очередь и настроить их выполнение в конце транзакции, включающей удаление. Правила Deleting всегда выполняются перед любыми присутствующими в очереди правилами Deleted.

     Используйте правила для распространения изменений, которые влияют только на элементы в хранилище, включая отношения, элементы схемы и их свойства. Обычно правило Deleting используется для распространения удаления, а правило Deleted — для создания элементов и отношений замены.

     Дополнительные сведения см. [в разделе правила распространяют изменения в модели](../modeling/rules-propagate-changes-within-the-model.md).

2. Событие **deleted** Store вызывается в конце транзакции и вызывается после отмены или повтора. Таким образом, его можно использовать для распространения удалений на объекты за пределами хранилища, например файлы, записи баз данных или другие объекты в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

     Дополнительные сведения см. в разделе " [обработчики событий" распространяют изменения за пределы модели](../modeling/event-handlers-propagate-changes-outside-the-model.md).

    > [!WARNING]
    > После удаления элемента можно получить доступ к его значениям свойства домена, но нельзя найти его связи отношений. Если же настроить событие Deleted на отношение, можно также получить доступ к двум элементам, которые были его исполнителями роли. Таким образом, если вам нужно ответить на удаление элемента модели, но требуется доступ к элементу, с которым он был связан, настройте событие удаления на отношение, а не на класс домена элемента модели.

### <a name="example-deletion-rules"></a>Пример правил Deletion

```
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletingRule : DeletingRule
{
  public override void ElementDeleting(ElementDeletingEventArgs e)
  {
    base.ElementDeleting(e);
    // ...perform tasks to propagate imminent deletion
  }
}
[RuleOn(typeof(Album), FireTime = TimeToFire.TopLevelCommit)]
internal class AlbumDeletedRule : DeleteRule
{
  public override void ElementDeleted(ElementDeletedEventArgs e)
  {
    base.ElementDeleted(e);
    // ...perform tasks such as creating new elements
  }
}

// The rule must be registered:
public partial class MusicLibDomainModel
{
  protected override Type[] GetCustomDomainModelTypes()
  {
    List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
    types.Add(typeof(AlbumDeletingRule));
    types.Add(typeof(AlbumDeletedRule));
    // If you add more rules, list them here.
    return types.ToArray();
  }
}

```

### <a name="example-deleted-event"></a>Пример события Deleted

```
partial class NestedShapesSampleDocData
{
  protected override void OnDocumentLoaded(EventArgs e)
  {
    base.OnDocumentLoaded(e);
    DomainRelationshipInfo commentRelationship =
          this.Store.DomainDataDirectory
          .FindDomainRelationship(typeof(CommentsReferenceComponents));

    this.Store.EventManagerDirectory.ElementDeleted.Add(commentRelationship,
      new EventHandler<ElementDeletedEventArgs>(CommentLinkDeleted));
  }

  private void CommentLinkDeleted (object sender, ElementDeletedEventArgs e)
  {
    CommentsReferenceComponents link = e.ModelElement as CommentsReferenceComponents;
    Comment comment = link.Comment;
    Component component = link.Subject;
    if (comment.IsDeleted)
    {
      // The link was deleted because the comment was deleted.
      System.Windows.Forms.MessageBox.Show("Removed comment on " + component.Name);
    }
    else
    {
      // It was just the link that was deleted - the comment itself remains.
      System.Windows.Forms.MessageBox.Show("Removed comment link to "
           + component.Name);
    }
  }
}

```

## <a name="unmerge"></a>Отменить объединение
 Операция, которая присоединяет дочерний элемент к его родителю, называется *Merge*. Она выполняется, когда новый элемент или группа элементов создаются с панели элементов, перемещаются из другой части модели или копируются из буфера обмена. Как и создание внедренного отношения между родительским и дочерним элементами, операция слияния может формировать дополнительные отношения, создавать вспомогательные элементы и задавать значения свойств в элементах. Операция слияния инкапсулируется в директиву слияния элементов (EMD).

 ЕМД также инкапсулирует дополняющую операцию *unmerge* или `MergeDisconnect`. Для удаления элемента из кластера, сконструированного путем слияния, с сохранением остальных элементов в согласованном состоянии рекомендуется использовать связанное разъединение. Операция разъединения обычно использует технологии, описанные в предыдущих разделах.

 Дополнительные сведения см. в разделе [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>См. также раздел
 [Настройка поведения копирования](../modeling/customizing-copy-behavior.md) [Настройка создания и перемещения элементов](../modeling/customizing-element-creation-and-movement.md) , [написание кода для настройки предметно-ориентированного языка](../modeling/writing-code-to-customise-a-domain-specific-language.md)
